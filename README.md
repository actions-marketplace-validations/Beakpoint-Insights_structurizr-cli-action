# bkpt-structurizr-cli GitHub Action

This GitHub action allows you to run [structurizr-cli](https://github.com/structurizr/cli), a command line utility for [Structurizr](https://structurizr.com/) that lets you create software architecture models based upon the [C4 model](https://c4model.com/) using a textual [domain specific language (DSL)](https://github.com/structurizr/dsl).

Currently, the action supports the following functionality:

- __Push__ content to a Structurizr workspace (the cloud service or an on-premises installation)
  - A model and views defined using the [Structurizr DSL](https://github.com/structurizr/dsl)
  - Markdown/AsciiDoc documentation
  - Architecture Decision Records (ADRs)

## Usage

To use the action simply create an `structurizr-cli.yml` (or choose custom `*.yml` name) in the `.github/workflows/` directory.

For example:

```yaml
name: sctructurizr-cli  # feel free to pick your own name

on: [push, pull_request]

jobs:
  structurizr-cli:
    runs-on: ubuntu-latest
    name: Run bkpt-structurizr-cli
    steps:

      - name: Checkout
        uses: actions/checkout@v2

      - name: Run bkpt-structurizr-cli action
        uses: aidmax/structurizr-cli-action@v1
        id: test
        with:
          id: # The workspace ID (required)
          key: # The workspace API key (required)
          secret: # The workspace API secret (required)
          workspace: # The path to the workspace JSON file/DSL file(s) (required)

          # optional parameters
          url: # The Structurizr API URL (optional; defaults to https://api.structurizr.com)
          passphrase: # The passphrase to use (optional; only required if client-side encryption enabled on the workspace)
          merge: # Whether to merge layout information from the remote workspace (optional: defaults to true)
          archive: # Whether to store the previous version of the remote workspace (optional; default to true)
          branch: # To tell Structurizr Cloud the name of the branch
```

## License

The Dockerfile and associated scripts and documentation in this project are released under the [MIT](license).

## Credits

The initial GitHub action was been created by [Maksim Milykh](https://github.com/aidmax).
