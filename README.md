# Google Cloud Storage or Azure Cache Action

This composite action will decide weither use gcs or azure cache.

- gcs is used for self-hosted runner
- azure is used for github runner

## Usage

> workflow.yml

```yaml
- name: Cache the node_modules
  id: node-modules-cache
  uses: kopax-polyconseil/gcs-or-azure-cache-action@v1
  with:
    bucket: my-ci-cache
    path: node_modules
    key: node-modules-${{ runner.os }}-${{ hashFiles('package-lock.json') }}
    restore-keys: |
      node-modules-${{ runner.os }}-${{ hashFiles('package-lock.json') }}
```

This composite action use under the hood the two following actions:

- gcs: https://github.com/kopax-polyconseil/gcs-cache-action
- azure: https://github.com/actions/cache

Read their documentation for all inputs.

## License

This project is [MIT licensed](LICENSE.txt).
