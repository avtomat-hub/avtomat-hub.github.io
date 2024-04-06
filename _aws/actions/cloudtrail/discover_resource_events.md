---
title: Discover Resource Events
parent: cloudtrail
grand_parent: Actions
layout: default
permalink: /aws/actions/cloudtrail/discover_resource_events
---

# Discover Resource Events

Discover events for a specific resource.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/cloudtrail/discover_resource_events.py">Source code</a> •
   <a href="/aws/permissions/cloudtrail/discover_resource_events">Permissions</a>
</p>

{: .note}
If **created_before** and **created_after** are not supplied, events are fetched for the last 90 days.

{: .warning}
This action will fetch all events against a resource in the specified time period and then filter for supplied
events.<br/>
If you are looking to find a specific event, use [Discover Events](/aws/actions/cloudtrail/discover_events) instead.

{: .note}
For a list of event names, see [Event Names](/aws/actions/cloudtrail/event_names).

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                              | Type           | Required | Default Value   |
|------------------|----------------------------------------------------------|----------------|----------|-----------------|
| `resource_id`    | Search events affecting this resource                    | `string`       | Yes      | None            |
| `events`         | Search for specific events                               | `list(string)` | No       | None            |
| `created_after`  | Search for events created after this time. (YYYY/MM/DD)  | `string`       | No       | None            |
| `created_before` | Search for events created before this time. (YYYY/MM/DD) | `string`       | No       | None            |
| `region`         | Region for operation. Leave blank for session default    | `string`       | No       | Session Default |
| `debug`          | Increase log verbosity                                   | `bool`         | No       | False           |
| `silent`         | Decrease log verbosity                                   | `bool`         | No       | False           |
| `session`        | Established session                                      | `object`       | No       | None            |                           

### Output

Returns a `list of objects` containing discovered events:

```python
[
    {
        'UserName': 'foo',
        'EventTime': '2021-01-01T00:00:00Z',
        'EventName': 'DetachVolume',
        'Resources': '["vol-1234567890abcdef0", "i-1234567890abcdef0"]'
    }
]
```

<div markdown="1" id="cli" style="display: block;">

## Examples

Discover any events against 'vol-1234567890abcdef0' created in the last 90 days in eu-west-2:

```bash
aaws cloudtrail discover_resource_events --resource_id vol-1234567890abcdef0 --region eu-west-2
```

Discover any 'DetachVolume' events against 'vol-1234567890abcdef0' in eu-west-2 between Jan 5, 2024 and Jan 10, 2024:

```bash
aaws cloudtrail discover_resource_events --resource_id vol-1234567890abcdef0 --events DetachVolume --created_before 2024/01/10 --created_after 2024/01/05 --region eu-west-2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover any events against 'vol-1234567890abcdef0' created in the last 90 days in eu-west-2:

```python
from avtomat_aws import cloudtrail

response = cloudtrail.discover_resource_events(resource_id="vol-1234567890abcdef0", region="eu-west-2")
```

Discover any 'DetachVolume' events against 'vol-1234567890abcdef0' in eu-west-2 between Jan 5, 2024 and Jan 10, 2024:

```python
from avtomat_aws import cloudtrail

response = cloudtrail.discover_resource_events(resource_id="vol-1234567890abcdef0",
                                               events=["DetachVolume"],
                                               created_before="2024/01/10",
                                               created_after="2024/01/05",
                                               region="eu-west-2")
```

</div>

<script>
  function toggleTables() {
    var cli = document.getElementById("cli");
    var prog = document.getElementById("prog");
    var toggleButton = document.getElementById("toggleButton");
    if (cli.style.display === "none") {
      cli.style.display = "block";
      prog.style.display = "none";
      toggleButton.innerHTML = "CLI";
    } else {
      cli.style.display = "none";
      prog.style.display = "block";
      toggleButton.innerHTML = "Programmatic";
    } 
  }
</script>
