# Download release

The public release page is used for release notes and downloadable artifacts.

## Latest release

Download the latest public release from:

```text
https://github.com/flik-lab/layang-odds/releases/latest
```

## Install RPM package

If an RPM artifact is attached to the release, download it and install it with:

```bash
sudo dnf install ./layang-odds-*.rpm
```

Or reinstall an existing version with:

```bash
sudo dnf reinstall ./layang-odds-*.rpm
```

## After install

1. Open Layang ODDS.
2. Let the DDS Runtime Build check finish.
3. Import the required `.idl` files.
4. Rebuild the DDS runtime sidecar if the workspace asks for it.
5. Scan Discovery and start testing DDS topics.

## Notes

- The public repository contains documentation and release notes.
- Source access is available by request for selected collaborators and integration partners.
- Do not upload private IDL files or internal DDS configuration to public issues.
