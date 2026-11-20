# Contracts & Data Models: [Назва Фічі]

## 1. Database Schema & Migrations

### Migration Script: `20261120_add_google_id_to_users.sql`
```sql
ALTER TABLE users
ADD COLUMN google_id VARCHAR(255) UNIQUE NULL,
ADD COLUMN auth_provider VARCHAR(50) DEFAULT 'email' NOT NULL;

CREATE INDEX idx_users_google_id ON users(google_id);
```

## 2. API Specifications (OpenAPI / REST)
`POST /api/v1/auth/google`

- **Request Body**:
```json
{
  "id_token": "eyJhbGciOiJSUzI1NiIs..."
}
```

- **Response 200 OK**:
```json
{
  "access_token": "ey...",
  "token_type": "Bearer",
  "expires_in": 3600,
  "user": {
    "id": "usr_12345",
    "email": "user@example.com",
    "name": "Alex Smith"
  }
}
```

- **Response 401 Unauthorized**:
```json
{
  "type": "https://api.example.com/errors/invalid-token",
  "title": "Invalid ID Token",
  "status": 401,
  "detail": "Google ID token has expired or is invalid."
}
```
