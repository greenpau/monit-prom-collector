# monit-prometheus-collector

The `m2p` tool allows to convert `monit status` output into Prometheus metrics.
The output of the tool is a `.prom` file. The file is designed to be consumed
by Prometheus [Node Exporter](https://github.com/prometheus/node_exporter)'s
[`textfile collector`](https://github.com/prometheus/node_exporter#textfile-collector).

The collector searches for `.prom` files inside the directory passed to
Node Exporter via `--collector.textfile.directory` flag.

Typically, Node Exporter with textfile collector enable starts in the following way:

```
/usr/sbin/node_exporter --collector.textfile.directory=/var/lib/prometheus
```

## Getting Started

The below parses the output of `monit` and creates `/var/lib/prometheus/localhost.monit.prom` file.

```
monit status | m2p --output /var/lib/prometheus/ --file localhost.monit
```

Also, a user may invoke the tool without sending the output of `monit status` to a pipe:

```
m2p --output /var/lib/prometheus/ --file localhost.monit
```
