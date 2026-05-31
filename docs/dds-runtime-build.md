# DDS Runtime Build

DDS Runtime Build validates or rebuilds the workspace sidecar used for imported IDL types.

## OpenDDS environment requirement

DDS Runtime Build needs access to OpenDDS tools from the active environment. Configure OpenDDS with one of these env files before running the build.

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

After editing the env file, restart Layang ODDS and run the DDS Runtime Build check again.

## Startup behavior

On app startup, Layang ODDS should:

1. Open the DDS Runtime Build status dialog.
2. Check workspace IDL sync.
3. Check runtime sidecar manifest/signature.
4. Skip rebuild if the current sidecar is valid.
5. Rebuild if IDL changed, the manifest is stale, or sidecar artifacts are missing.
6. Load the sidecar once it is ready.

## Dialog behavior

The dialog should clearly show whether the runtime is:

- checking
- building
- ready
- failed

When the check/build has finished, the dialog should offer:

- **Rebuild again**
- **Close**

## Common issue

If DDS Listener reports that a TypeSupport adapter is missing, it usually means the active runtime sidecar or main app build does not contain the imported IDL type. Rebuild the DDS runtime for the active workspace and retry.
