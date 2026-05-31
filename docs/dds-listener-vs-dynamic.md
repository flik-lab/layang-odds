# DDS Listener vs Dynamic

Layang ODDS has two subscriber modes.

## DDS Listener

DDS Listener is the typed subscription path. It is preferred for production workflows when the IDL is available.

Use DDS Listener when:

- the topic type is known from imported IDL
- you need stable typed decoding
- remote XTypes support is not reliable
- you plan to publish or stream typed samples

## Dynamic

Dynamic mode uses XTypes/DynamicData-style monitoring.

Use Dynamic when:

- the remote DDS participant provides dynamic type information
- you only need to inspect samples
- IDL is not available yet

## Recommendation

For production testing, import IDL and use DDS Listener. Keep Dynamic as a fallback or discovery aid.
