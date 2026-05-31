# Import IDL

Use the IDL panel to import `.idl` files into the active workspace.

## Expected flow

1. Click **Import IDL**.
2. Select an `.idl` file from the file picker.
3. Wait for the workspace sync and runtime build check.
4. Confirm the DDS Runtime Build dialog reports ready or completed.
5. Open the mapped topic from Discovery or IDL mapping.

## Requirements

IDL files intended for DDS publish/subscribe should declare topic types using the expected OpenDDS annotations or pragmas used by your DDS environment.

## After import

After importing IDL, the runtime build should check whether the workspace sidecar is up to date. If the IDL changed or sidecar artifacts are missing, a rebuild is needed before DDS Listener or typed publish/stream can run.
