# Restorely Dashboard

### Waited data from API
```json
[
  {
    "id": "db_1",
    "name": "production",
    "type": "postgres",
    "last_backup": {
      "status": "success",
      "created_at": "2025-01-10T02:00:00Z",
      "duration_ms": 32000
    },
    "last_restore_test": {
      "status": "success",
      "created_at": "2025-01-09T03:00:00Z",
      "duration_ms": 45000
    }
  }
]
```

### Onboarding database
```psql
UI (Vue)
  │
  ▼
POST /databases
  │
  ├─ validate input
  ├─ test connection (ping DB)
  └─ insert database
```
