---
title: Discover Events
parent: cloudtrail
grand_parent: Actions
layout: default
permalink: /aws/actions/cloudtrail/discover_events
---

# Discover Events

Discover events by name.

<p align="center">
   <a href="https://github.com/avtomat-hub/avtomat-aws/tree/main/avtomat_aws/services/cloudtrail/discover_events.py">Source code</a> •
   <a href="/aws/permissions/cloudtrail/discover_events">Permissions</a>
</p>

{: .note}
If **created_before** and **created_after** are not supplied, events are fetched for the last 90 days.

{: .note}
For a list of event names, see [Event Names](/aws/actions/cloudtrail/event_names).

## Usage <button id="toggleButton" class="btn fs-3" onclick="toggleTables()">CLI</button>

### Input

| Parameter        | Description                                              | Type     | Required | Default Value   |
|------------------|----------------------------------------------------------|----------|----------|-----------------|
| `event`          | Search for this event                                    | `string` | Yes      | None            |
| `created_after`  | Search for events created after this time. (YYYY/MM/DD)  | `string` | No       | None            |
| `created_before` | Search for events created before this time. (YYYY/MM/DD) | `string` | No       | None            |
| `region`         | Region for operation. Leave blank for session default    | `string` | No       | Session Default |
| `debug`          | Increase log verbosity                                   | `bool`   | No       | False           |
| `silent`         | Decrease log verbosity                                   | `bool`   | No       | False           |
| `session`        | Established session                                      | `object` | No       | None            |                           

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

Discover 'TerminateInstances' events created in the last 90 days in eu-west-2:

```bash
aaws cloudtrail discover_events --event TerminateInstances --region eu-west-2
```

Discover 'DetachVolume' events between Jan 5, 2024 and Jan 10, 2024 in eu-west-2:

```bash
aaws cloudtrail discover_events --event DetachVolume --created_before 2024/01/10 --created_after 2024/01/05 --region eu-west-2
```

</div>

<div markdown="1" id="prog" style="display: none;">

## Examples

Discover 'TerminateInstances' events created in the last 90 days in eu-west-2:

```python
from avtomat_aws import cloudtrail

response = cloudtrail.discover_events(event="TerminateInstances", region="eu-west-2")
```

Discover 'DetachVolume' events between Jan 5, 2024 and Jan 10, 2024 in eu-west-2:

```python
from avtomat_aws import cloudtrail

response = cloudtrail.discover_events(event="DetachVolume",
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
