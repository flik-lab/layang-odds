# OpenDDS environment

Layang ODDS reads DDS runtime settings from env files when the packaged app starts.

You can configure OpenDDS in two ways:

- **User config**: recommended for normal desktop usage.
- **System-wide config**: useful for shared machines, lab PCs, or admin-managed installs.

Manual shell `export` commands are not required when launching the packaged app.

## Option 1: User config, recommended

Edit the per-user env file:

```bash
mkdir -p ~/.config/layang-odds
nano ~/.config/layang-odds/env
```

Example content:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=$HOME/.config/layang-odds/rtps.ini
```

Use this option when each Linux user may have a different OpenDDS path or DDS config.

## Option 2: System-wide config

Edit the system-wide env file:

```bash
sudo mkdir -p /etc/layang-odds
sudo nano /etc/layang-odds/layang-odds.env
```

Example content:

```dotenv
OPENDDS_ROOT=/opt/OpenDDS-3.29.1
LAYANG_ODDS_DDS_CONFIG=/home/rocky/.config/layang-odds/rtps.ini
```

Use this option when the same OpenDDS installation is shared by all users on the machine.

## Priority

The packaged app launcher loads env files in this order:

```text
1. Packaged default env
2. /etc/layang-odds/layang-odds.env
3. ~/.config/layang-odds/env
```

The user config is loaded last, so it can override the system-wide config.

## Create the RTPS config file

If the RTPS config file does not exist yet, create it:

```bash
mkdir -p ~/.config/layang-odds
nano ~/.config/layang-odds/rtps.ini
```

Example `rtps.ini`:

```ini
[common]
DCPSGlobalTransportConfig=$file
DCPSDefaultDiscovery=DEFAULT_RTPS

[rtps_discovery/DEFAULT_RTPS]
SedpMulticast=1
ResendPeriod=2

[transport/the_rtps_transport]
transport_type=rtps_udp
use_multicast=1
```

## Apply the change

After editing the env file:

1. Restart Layang ODDS.
2. Open **DDS Runtime Build**.
3. Let the runtime check finish.
4. Click **Rebuild again** only if the runtime sidecar is stale, missing, or the IDL changed.

## Notes

- `OPENDDS_ROOT` must point to a complete OpenDDS development/source tree.
- The OpenDDS tree should contain `setenv.sh`, `cmake/OpenDDSConfig.cmake`, `bin/opendds_idl`, `dds/`, and `ACE_wrappers/`.
- Restart the app after editing the env file.
- Manual shell exports are only for development shells or custom launchers.
