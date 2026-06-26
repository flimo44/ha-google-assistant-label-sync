# HA Google Assistant Label Sync

Generate Home Assistant Google Assistant `entity_config` from Home Assistant labels.

Instead of manually maintaining a long YAML list of exposed entities, simply add a label in Home Assistant, run the script, and it generates the Google Assistant configuration automatically.

## Features

- Select entities using a Home Assistant label
- Generate `entity_config` for Google Assistant
- Use Home Assistant friendly names
- Use Home Assistant areas as Google rooms
- Ignore disabled or hidden entities
- Dry-run mode before writing the file
<img width="1080" height="2400" alt="Screenshot_2026-06-26-19-44-33-60_2d2bd67b5e15ae98c151ac739cd6881e" src="https://github.com/user-attachments/assets/a03d1005-fde8-4186-b8ea-da2f426c5a84" />

```
Home Assistant
        │
        ▼
Labels
        │
        ▼
Voice Assistant Sync
        │
 ┌──────┴───────┐
 │              │
Google       Alexa
```

## Example output

```yaml
switch.prise_pompe:
  expose: true
  name: Pompe piscine
  room: Piscine
```


Home Assistant configuration

```yaml
google_assistant:
  project_id: YOUR_PROJECT_ID
  service_account: !include google_key.json
  report_state: true
  expose_by_default: false
  entity_config: !include google_assistant_entities.yaml
```

Usage

python3 /config/scripts/ga_label_sync.py --label "google_assistant" --dry-run

Generate the file:

python3 /config/scripts/ga_label_sync.py --label "google_assistant"

<img width="1080" height="2400" alt="Screenshot_2026-06-26-19-45-48-86_2d2bd67b5e15ae98c151ac739cd6881e" src="https://github.com/user-attachments/assets/5b4d96cc-9da9-4419-9d1f-f5eac4fbec8c" />

License
MIT
