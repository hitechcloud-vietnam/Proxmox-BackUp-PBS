# Proxmox Backup Server (PBS) — Full API Collection

Complete REST API collection for Proxmox Backup Server (PBS) with ready-to-use requests for datastore management, snapshots, maintenance operations, sync jobs, tape backup, access control, and backup protocol operations.

---

## Features

* 🔐 API Token & Ticket Authentication
* 📊 Node Status & System Information
* 🗄️ Datastore Management
* 📦 Snapshot & Backup Group Operations
* 🔧 Garbage Collection, Verify & Prune Jobs
* 📡 Remote Sync & Replication
* 👥 Users, ACL & Roles Management
* ⚙️ Network & Notification Configuration
* 📼 Tape Backup Management
* 🔁 Backup Protocol API
* 📖 Reader Protocol API

---

## API Information

| Item           | Value                                  |
| -------------- | -------------------------------------- |
| Base URL       | `https://your-pbs-host:8007/api2/json` |
| Protocol       | HTTPS                                  |
| Default Port   | `8007`                                 |
| Authentication | `PBSAPIToken` or Ticket + CSRF         |
| SSL            | Self-signed certificate supported      |

---

## Authentication Methods

### API Token Authentication

```http
Authorization: PBSAPIToken=root@pam!mytoken:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

### Ticket-Based Login

#### Request

```http
POST /api2/json/access/ticket
```

#### Response

```json
{
  "data": {
    "ticket": "PBS:root@pam:XXXXXXXX::...",
    "CSRFPreventionToken": "XXXXXXXX:..."
  }
}
```

#### Usage

```http
Cookie: PBSAuthCookie=<ticket>
CSRFPreventionToken: <token>
```

---

## Included Modules

| Module             | Description             |
| ------------------ | ----------------------- |
| Auth               | Login & API Tokens      |
| Status & Nodes     | System Status & Metrics |
| Datastores         | Storage Management      |
| Snapshots & Groups | Backup Snapshots        |
| Maintenance        | GC, Verify & Prune      |
| Sync & Remote      | Remote Sync Jobs        |
| Access Control     | Users, ACL & Roles      |
| Configuration      | Network & Notifications |
| Tape Backup        | Tape Libraries & Jobs   |
| Backup Protocol    | HTTP/2 Backup Upload    |
| Reader Protocol    | HTTP/2 Restore Access   |

---

## Supported API Clients

* Postman
* Insomnia
* Bruno

---

## Notes

* PBS uses HTTPS on port `8007`
* Default installations commonly use self-signed SSL certificates
* Most write operations require `CSRFPreventionToken`
* For curl requests, `--insecure` may be required
* API Token format:

```text
PBSAPIToken=user@realm!tokenname:tokensecret
```

---

## Official Documentation

* https://pbs.proxmox.com/docs/api-viewer/index.html
* https://pbs.proxmox.com/docs/backup-protocol.html

---

## License

MIT License.

Use freely for automation, monitoring, backup orchestration, hosting platforms, and integrations.
