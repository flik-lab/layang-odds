# Discovery and mapping

The Discovery panel scans DDS topics from the network and shows discovered or locally mapped topics.

## Duplicate topic names

Layang ODDS treats a topic as unique by:

```text
domainId + topicName + typeName
```

If two entries have the same topic name but different types, they stay separate. The UI may show a duplicate-name badge so the operator can confirm the correct type before subscribing or publishing.

## Recommended behavior

- Same topic name and same type: merge as one topic.
- Same topic name and different type: keep separate.
- Same topic name and different domain: keep separate.
- Subscribe, publish, and stream requests should carry topic name, type name, domain id, and topic key.

## Operator checklist

1. Scan Discovery.
2. Check the type name under each topic.
3. Prefer DDS Listener for imported IDL/mapped topics.
4. Use Dynamic only when remote XTypes data is available and reliable.
5. For duplicate names, always confirm the type before running a stream.
