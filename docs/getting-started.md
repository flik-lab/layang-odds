# Getting started

Layang ODDS is a DDS desktop workflow for operators and developers who need to inspect DDS topics, import IDL, subscribe to live samples, publish JSON payloads, and run scenario streams.

## Download

Download release artifacts from:

```text
https://github.com/flik-lab/layang-odds/releases/latest
```

If an RPM is attached to the release, install it with:

```bash
sudo dnf install ./layang-odds-*.rpm
```

## OpenDDS environment

Choose one env config option before opening Layang ODDS.

### Option 1: User config, recommended

```bash
mkdir -p ~/.config/layang-odds
nano ~/.config/layang-odds/env
```

Example:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=$HOME/.config/layang-odds/rtps.ini
```

### Option 2: System-wide config

```bash
sudo mkdir -p /etc/layang-odds
sudo nano /etc/layang-odds/layang-odds.env
```

Example:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=/home/rocky/.config/layang-odds/rtps.ini
```

Restart Layang ODDS after editing the env file. See [OpenDDS environment](opendds-environment.md) for details.

## Main workflow

1. Open Layang ODDS.
2. Let the DDS Runtime Build check finish.
3. Import `.idl` files when typed DDS Listener support is needed.
4. Scan Discovery.
5. Open a discovered or mapped topic.
6. Choose Subscriber mode: DDS Listener or Dynamic.
7. Subscribe, publish once, or start a scenario stream.
8. Inspect latest sample, response, event, and runtime status.

## Key concepts

| Concept | Meaning |
|---|---|
| Discovery | Network scan of DDS topics and topic types. |
| Local mapped topic | A topic created from imported IDL metadata. |
| DDS Listener | Typed listener path using TypeSupport generated from IDL. |
| Dynamic | XTypes/DynamicData monitor path when remote dynamic data is available. |
| Scenario stream | Ordered JSON sample array published repeatedly or once. |
| DDS Runtime Build | Workspace sidecar build/check used after importing IDL. |

## Topic identity

Topic identity uses:

```text
domainId + topicName + typeName
```

This avoids conflicts when two DDS topics share the same topic name but use different IDL types.
