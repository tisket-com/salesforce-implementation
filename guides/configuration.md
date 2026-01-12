# Salesforce Configuration Guide

## Prerequisites

- Salesforce Enterprise Edition or higher
- System Administrator access in Salesforce
- Tisket Admin role

## Setup Steps

### 1. Create Connected App in Salesforce

1. Navigate to Setup → Apps → App Manager
2. Click "New Connected App"
3. Configure:
   - **App Name**: Tisket Integration
   - **API Name**: Tisket_Integration
   - **Contact Email**: your-email@company.com
4. Enable OAuth Settings:
   - **Callback URL**: `https://app.tisket.com/integrations/salesforce/callback`
   - **Selected Scopes**: api, refresh_token, openid
5. Save and note the Consumer Key and Secret

### 2. Connect in Tisket

1. Go to Settings → Integrations → Salesforce
2. Click "Connect Salesforce"
3. Enter your Salesforce instance URL
4. Authorize the connection
5. Select sync options

## Sync Configuration

### Field Mapping

Configure which Tisket fields map to Salesforce fields:

| Tisket Field | Salesforce Field |
|--------------|------------------|
| Full Name | Name |
| Email | Email |
| Company | Account.Name |
| Phone | Phone |

### Sync Frequency

- **Real-time**: Immediate sync via webhooks
- **Scheduled**: Hourly batch sync for reconciliation

## Troubleshooting

### Connection Issues
- Verify Connected App is active
- Check IP restrictions in Salesforce
- Confirm OAuth scopes match

### Sync Failures
- Review error logs in Settings → Integrations → Logs
- Check field validation rules in Salesforce
- Verify user has write permissions
