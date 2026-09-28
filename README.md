# soktalk-logging

Git-backed source of truth for the Promtail/Loki logging stack on the doksok cluster.

## Structure

```
promtail/
└── config.yaml    # Promtail configuration (synced into ConfigMap promtail-config)
```

## Sync

Promtail reads its config from ConfigMap `promtail-config` in the `loki` namespace.
A git-sync sidecar pulls this repo into an emptyDir and a small init container renders
the file into the ConfigMap (or the file is mounted directly as a volume).

## Local extraction

```bash
python3 deploy/extract-configs.py
```
