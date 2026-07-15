# Items

An item belongs to a single owner and has a title, an optional description, and an optional priority. Every item is returned to the client with its ID, owner ID, and creation timestamp in addition to the fields you set.

## Fields

| Field | Type | Constraints | Description |
|---|---|---|---|
| `title` | string | 1–255 characters, required | The display name of the item. |
| `description` | string or null | Maximum 255 characters | An optional free-text description of the item. |
| `priority` | integer or null | 1–5 | Triage priority from 1 (highest) to 5 (lowest); introduced to support the triage workflow. |
| `id` | UUID string | read-only, required | The unique identifier assigned to the item by the server. |
| `owner_id` | UUID string | read-only, required | The unique identifier of the user who owns the item. |
| `created_at` | datetime string or null | read-only | The UTC timestamp at which the item was created. |

## Creating and updating items

Send a `title` and, optionally, a `description` and a `priority` to create an item. The title must be between 1 and 255 characters. The `priority` field accepts an integer from 1 (highest urgency) to 5 (lowest urgency); omit it or send `null` to leave priority unset.

Updates use `PUT /api/v1/items/{id}` and accept `title` and `description`. Include only the fields you want to change; omit a field to leave its current value unchanged.