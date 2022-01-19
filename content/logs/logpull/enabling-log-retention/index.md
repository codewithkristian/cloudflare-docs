---
order: 12
pcx-content-type: interim
---

# Enabling log retention

By default, your HTTP request logs are not retained. When using the Logpull API for the first time, you will need to enable retention. You can also turn off retention at any time. Note that after retention is turned off, previously saved logs will be available until the retention period expires (_see [Data retention period](/logpull/understanding-the-basics/#data-retention-period)_).

## Endpoints

There are two endpoints for managing log retention:

- `GET /logs/control/retention/flag` - returns whether retention is on
- `POST /logs/control/retention/flag` - turns retention on or off

<bongo:aside type="note" header="Note">
To make a `POST` call, you must have a Cloudflare account role with "edit" permissions, such as Super Administrator, Administrator, or Log Share.
</bongo:aside>

## Example API requests using cURL

### Check whether log retention is turned on:

```bash
curl -s -H "X-Auth-Email: <REDACTED>" -H "X-Auth-Key: <REDACTED>" GET "https://api.cloudflare.com/client/v4/zones/<ZONE_ID>/logs/control/retention/flag" | jq .
```

#### Response

```json
{
  "errors": [],
  "messages": [],
  "result": {
    "flag": false
  },
  "success": true
}
```

### Turn on log retention:

```bash
curl -s -H "X-Auth-Email: <REDACTED>" -H "X-Auth-Key: <REDACTED>" POST "https://api.cloudflare.com/client/v4/zones/<ZONE_ID>/logs/control/retention/flag" -d'{"flag":true}' | jq .
```

#### Parameters

- _flag_ - can be either `true` or `false`

#### Response

```bash
{
  "errors": [],
  "messages": [],
  "result": {
    "flag": true
  },
  "success": true
}
```

## Audit

Turning log retention on or off is recorded in **Cloudflare Audit Logs**.