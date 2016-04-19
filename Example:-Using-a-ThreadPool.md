You have this amazingly tiny web server that works perfectly! But wait, what happens when it gets a million simultaneous requests? Do you want to spin up a million threads? No. You want a thread pool. Something like this:
```java
package com.switchboard.tools;

import fi.iki.elonen.NanoHTTPD;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.concurrent.ExecutorService;

/**
 * BoundRunner
 * <p>
 * The default threading strategy for NanoHTTPD launches a new thread every time. We override that here so we can put an
 * upper limit on the number of active threads using a thread pool.
 */
class BoundRunner implements NanoHTTPD.AsyncRunner {
    private ExecutorService executorService;
    private final List<NanoHTTPD.ClientHandler> running =
            Collections.synchronizedList(new ArrayList<NanoHTTPD.ClientHandler>());

    public BoundRunner(ExecutorService executorService) {
        this.executorService = executorService;
    }

    @Override
    public void closeAll() {
        // copy of the list for concurrency
        for (NanoHTTPD.ClientHandler clientHandler : new ArrayList<>(this.running)) {
            clientHandler.close();
        }
    }

    @Override
    public void closed(NanoHTTPD.ClientHandler clientHandler) {
        this.running.remove(clientHandler);
    }

    @Override
    public void exec(NanoHTTPD.ClientHandler clientHandler) {
        executorService.submit(clientHandler);
        this.running.add(clientHandler);
    }
}
```

You use it with something like

```java
import fi.iki.elonen.NanoHTTPD;
import org.apache.commons.cli.BasicParser;
import org.apache.commons.cli.CommandLine;
import org.apache.commons.cli.CommandLineParser;
import org.apache.commons.cli.Options;

import java.io.IOException;
import java.util.concurrent.Executors;
import java.util.logging.Level;
import java.util.logging.Logger;

/** App is a simple little web server devoted to running NormalizeCSV.normalize with some constraints on the
 *  number of threads */
public class App extends NanoHTTPD {

    private static final Logger logger = Logger.getLogger(App.class.getName());

    public App(int port) throws IOException {
        super(port);
    }

    public static void main(String[] args) {
        try {

            Options options = new Options();
            options.addOption("port", true, "port number to use");
            options.addOption("web_threads", true, "maximum number of threads for the web server");

            CommandLineParser parser = new BasicParser();
            CommandLine cmd = parser.parse(options, args);

            int port = Integer.parseInt(cmd.getOptionValue("port", "5375"));
            int webThreads = Integer.parseInt(cmd.getOptionValue("web_threads", "10"));

            App app = new App(port);
            app.setAsyncRunner(new BoundRunner(Executors.newFixedThreadPool(webThreads)));
            app.start(NanoHTTPD.SOCKET_READ_TIMEOUT, false);
            logger.info("waiting for connections on port " + port + " using a maximum of " + gzipThreads +
                    " gzip threads and " + webThreads + " web threads");

        } catch (Throwable t) {
            logger.log(Level.SEVERE, "Couldn't start server", t);
            System.exit(1);
        }
    }
}
```