# Backend API Documentation

## Base URL

`http://localhost:5000`

## Public routes

### `GET /api/health`
Returns API health status.

### `GET /api/early-bird-status`
Returns current early bird usage and remaining spots.

### `POST /api/register`
Creates a new membership registration.

Body:

```json
{
  "fullName": "Jordan Smith",
  "email": "jordan@example.com",
  "phone": "0212345678",
  "address": "123 Rose Street, Remuera",
  "existingCustomer": false,
  "preferredBranch": "Auckland City",
  "notes": "Would like a morning appointment",
  "termsAccepted": true,
  "marketingConsent": true
}
```

Validation rules:
- `fullName` required
- `email` valid email
- `phone` NZ mobile or landline
- `address` required
- `existingCustomer` boolean
- `termsAccepted` must be true

### Admin routes

### `POST /api/admin/login`
Authenticates an admin and returns a JWT.

### `GET /api/admin/registrations`
Returns paginated registrations. Supports filters:
- `search`
- `status`
- `existingCustomer`
- `startDate`
- `endDate`
- `page`
- `limit`

### `GET /api/admin/stats`
Returns total, daily, and pending registration counts.

### `PUT /api/admin/registration/:id`
Updates registration status and notes.

### `DELETE /api/admin/registration/:id`
Deletes a registration record.

### `GET /api/admin/export/csv`
Exports filtered registrations as CSV.

### `GET /api/admin/export/xlsx`
Exports filtered registrations as Excel.
