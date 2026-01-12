# Salesforce API Integration Guide

## Authentication

This integration uses Salesforce OAuth 2.0 Web Server Flow for secure authentication.

### Required Scopes
- `api` - Access REST API
- `refresh_token` - Offline access
- `openid` - OpenID Connect

### Configuration

Set the following environment variables:

```
SALESFORCE_CLIENT_ID=your_connected_app_client_id
SALESFORCE_CLIENT_SECRET=your_connected_app_secret
SALESFORCE_REDIRECT_URI=https://app.tisket.com/integrations/salesforce/callback
```

## API Endpoints

### Contacts

| Tisket Action | Salesforce API |
|---------------|----------------|
| Create Contact | `POST /services/data/v59.0/sobjects/Contact` |
| Update Contact | `PATCH /services/data/v59.0/sobjects/Contact/{id}` |
| Get Contact | `GET /services/data/v59.0/sobjects/Contact/{id}` |

### Leads

| Tisket Action | Salesforce API |
|---------------|----------------|
| Create Lead | `POST /services/data/v59.0/sobjects/Lead` |
| Convert Lead | `POST /services/data/v59.0/sobjects/Lead/{id}/convert` |

## Webhooks

Salesforce Platform Events are used for real-time sync:

- `Contact__e` - Contact changes
- `Lead__e` - Lead changes
- `Opportunity__e` - Opportunity updates

## Error Handling

All API errors are logged and retried with exponential backoff. Failed syncs are queued for manual review in the admin dashboard.
