# process-reporter

Reports information about your node process to statsd. Use it like this:

```javascript
var ProcessReporter = require('process-reporter');

var processReporter = ProcessReporter({
    statsd: statsdClient
});

processReporter.bootstrap();
```

It currently reports these stats:

* **yourapp.process-reporter.handles** number of libuv handles
* **yourapp.process-reporter.requests** number of libuv requests
* **yourapp.process-reporter.memory-usage.rss** resident set size of procss
* **yourapp.process-reporter.memory-usage.heap-total** total size of v8 heap
* **yourapp.process-reporter.memory-usage.heap-used** amt of v8 heap used
* **yourapp.process-reporter.lag-sampler** event loop lag
* **yourapp.process-reporter.gc.{gc-type}.pause-ms** length of GC pauses
* **yourapp.process-reporter.gc.{gc-type}.heap-used** +/- amount of bytes GCd
* **yourapp.process-reporter.gc.{gc-type}.heap-total** +/- changes in heap total

To destroy the reporter just call `processReporter.destroy();`
