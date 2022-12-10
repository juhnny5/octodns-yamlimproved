## YAMLimproved provider for octoDNS

An [octoDNS](https://github.com/octodns/octodns/) provider which brings additional features to the original YAML provider, including the ability to specify custom zone file names.

### Installation

#### Command line

```bash
pip install octodns-yamlimproved
```

#### requirements.txt/setup.py

Pinning specific versions or SHAs is recommended to avoid unplanned upgrades.

##### Versions

```
# Start with the latest versions and don't just copy what's here
octodns==0.9.14
octodns-yamlimproved==0.0.1
```

### Configuration

```yaml
providers:
    config:
        class: octodns_yamlimproved.YamlProvider
        # The location of yaml config files (required)
        directory: ./config
        # Specify a custom zone file name
        # File present in the directory declared in "directory" without specifying the extension.
        # (optional, default empty)
        file_name: "root"
        # The ttl to use for records when not specified in the data
        # (optional, default 3600)
        default_ttl: 3600
        # Whether or not to enforce sorting order on the yaml config
        # (optional, default True)
        enforce_order: true
        # Whether duplicate records should replace rather than error
        # (optiona, default False)
        populate_should_replace: false
```

### Support Information

#### Records

Supports A, AAAA, NS, MX, TXT, SRV, CNAME, and PTR.

#### Dynamic

YamlImprovedProvider does not support dynamic records.

### Development

See the [/script/](/script/) directory for some tools to help with the development process. They generally follow the [Script to rule them all](https://github.com/github/scripts-to-rule-them-all) pattern. Most useful is `./script/bootstrap` which will create a venv and install both the runtime and development related requirements. It will also hook up a pre-commit hook that covers most of what's run by CI.
