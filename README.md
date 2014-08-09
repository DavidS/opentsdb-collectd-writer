opentsdb-collectd-writer
========================

A python based bridge from collectd to opentsdb. You'll need to define mappings
for your local collectd values in `value_to_hash`, or accept the default
mapping.

To keep the load on the opentsdb low, the plugin implements a in-memory queue
for storing up to 1024 events that is flushed every 10s to the opentsdb host.
If you have more than 1024 events within 10s, you might want to increase that.

Configuration
=============

```
  ModulePath "/path/to/installed/tsdb.py"
  Import "tsdb"
  <Module tsdb>
    server "opentsdb server name"
    port   "https port of opentsdb server"
    ca     "ca file"
    cert   "local certificate"
    key    "local private key"
    tag    "host" "my host name"
    tag    "dc"   "my datacenter"
  </Module>
```

The tsdb plugin uses SSL certificates to authenticate against the opentsdb.

Using the `tag` configuration option, you can specify additional tags to be
added to all metrics.


