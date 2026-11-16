# RoomQ

RoomQ is a Node.js-served classroom scheduling and availability application. Its room inventory and plan coordinates come from the existing mapped layouts in `roomq-data.js`; schedule and reservation records are stored in SQLite.

## Requirements

- Node.js 24 or later

## Run locally

Set a private administrator password of at least 12 characters, then start the server:

```powershell
$env:ROOMQ_ADMIN_PASSWORD = "choose-a-private-password"
npm start
```

Open `http://localhost:3000`. The default administrator username is `admin`; set `ROOMQ_ADMIN_USERNAME` to change it. The SQLite database is created as `roomq.sqlite` and is intentionally excluded from source control.

The server binds to `127.0.0.1` by default. Set `HOST` and `PORT` explicitly only when deploying behind an HTTPS reverse proxy or when access from another machine is required. Set `ROOMQ_DB_PATH` to store the SQLite database at a custom path. Set `NODE_ENV=production` to enable the secure session-cookie attribute.

## Tests

```powershell
npm test
```

## Data notes

- The mapped buildings, floors, classroom positions, and names are shared from `roomq-data.js`; no room positions are generated.
- The project has no capacity/facility records or classroom mapping for LAW Rooms. Those values remain unavailable until real records are supplied.
- Passwords are stored as salted scrypt hashes. Schedule mutations require an administrator session.
- Browser-local room-use data from earlier versions is not automatically uploaded to the database.
