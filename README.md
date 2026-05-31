# Layang ODDS

Public documentation and release notes for **Layang ODDS**, an OpenDDS Simulator desktop workflow for DDS topic discovery, IDL mapping, DDS Listener/Dynamic subscription, JSON publishing, scenario streaming, and per-topic QoS checks.

Layang ODDS is designed to help developers, integrators, and DDS users test OpenDDS topic flows from a desktop application.

## Website

After enabling GitHub Pages, the public site should be available at:

```text
https://flik-lab.github.io/layang-odds/
```

## Download Release

Download the latest public release from:

```text
https://github.com/flik-lab/layang-odds/releases/latest
```

If an RPM artifact is available, install it with:

```bash
sudo dnf install ./layang-odds-*.rpm
```

See [Download release](docs/download-release.md) for release download and install notes.

## OpenDDS Environment

Layang ODDS can read OpenDDS settings from two env files. Use the user config for normal desktop usage, or system-wide config for shared/admin-managed machines. No manual shell `export` is required when launching the packaged app.

### Option 1: User config, recommended

```bash
mkdir -p ~/.config/layang-odds
nano ~/.config/layang-odds/env
```

Example content:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=$HOME/.config/layang-odds/rtps.ini
```

### Option 2: System-wide config

```bash
sudo nano /etc/layang-odds/layang-odds.env
```

Example content:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=/home/rocky/.config/layang-odds/rtps.ini
```

After changing an env file, restart Layang ODDS and run **DDS Runtime Build** again if the workspace IDL or runtime sidecar needs to be refreshed.

See [OpenDDS environment](docs/opendds-environment.md) for the full guide.

## Project Status

This repository is the **public documentation and release-notes repository** for Layang ODDS.

The main application source code is currently maintained in a private repository:

```text
layang-odds-source
```

Source access is limited for now and may be granted selectively for trusted collaborators, DDS/OpenDDS contributors, integration partners, or organizations evaluating Layang ODDS.

Public repository scope:

- documentation
- release notes
- screenshots
- usage guide
- known issues
- roadmap
- support information

Private source repository scope:

- CEF runtime source
- OpenDDS native integration
- DDS runtime sidecar
- IDL adapter generator
- native bridge implementation
- packaging and build scripts

## Docs

- [Getting started](docs/getting-started.md)
- [Download release](docs/download-release.md)
- [OpenDDS environment](docs/opendds-environment.md)
- [Discovery and mapping](docs/discovery-and-mapping.md)
- [Import IDL](docs/import-idl.md)
- [DDS runtime build](docs/dds-runtime-build.md)
- [DDS Listener vs Dynamic](docs/dds-listener-vs-dynamic.md)
- [Scenario stream](docs/scenario-stream.md)
- [QoS editor](docs/qos-editor.md)

## Release Notes

- [v1.0.0 public docs release](release-notes/v1.0.0.md)

## Support

Need help or want to collaborate?

Report issues, request features, discuss collaboration, or ask for source access.

- GitHub Issues: [flik-lab/layang-odds/issues](https://github.com/flik-lab/layang-odds/issues)
- GitHub: [@flik-lab](https://github.com/flik-lab)
- Email: [fliklabdev@gmail.com](mailto:fliklabdev@gmail.com)

## Source Access

The source code is not publicly available yet.

Source access may be granted selectively for:

- trusted collaborators
- DDS/OpenDDS testing contributors
- integration partners
- organizations evaluating Layang ODDS
- contributors working on approved issues or feature areas

Opening a public issue does not automatically grant source access. Please contact the maintainer for private source access discussion.

## Security and Confidentiality

Please do not include confidential data in public issues, including:

- private IDL files
- internal DDS configuration
- network addresses
- company-sensitive screenshots
- credentials, tokens, or license keys
- private logs from production systems

For sensitive reports or private integration details, use email instead.

## License

The public documentation in this repository may be shared for evaluation and reference.

The Layang ODDS application source code is private and is not covered by this public documentation repository.