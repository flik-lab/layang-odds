# Scenario stream

Scenario stream publishes one or more JSON payloads to a DDS topic.

## Basic flow

1. Open a topic tab.
2. Create or select a scenario.
3. Add JSON sample objects in the scenario array.
4. Set interval and loop count.
5. Start stream.
6. Stop stream when finished.

## Stability notes

A stream should be keyed by the full topic identity:

```text
domainId + topicName + typeName
```

This avoids stop/start conflicts when multiple DDS topics share the same visible topic name.

## Stop/start behavior

When stopping a stream, any in-flight publish request should be cancelled or allowed to finish quickly so that starting again does not hang on a stale sidecar request.
