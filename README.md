# Google JWT SA ✨
Get Google Auth Token for OAuth 2.0 for Server to Server Applications/Google APIs.

### Usage
```ts
import { GoogleAuth, GoogleJwtSa } from 'https://deno.land/x/googlejwtsa@{version}/mod.ts'

const googleServiceAccountCredentials = await Deno.readTextFile(
  filepath
)

const googleAuthOptions = {
  scope: ['<Google API Endpoint URLs>'], // array of Google's endpoint URLs
  sub: 'someone@yourdomian.com' // optional subject for domain delegation
}

const token: GoogleAuth = await GoogleJwtSa.getToken(
  googleServiceAccountCredentials, googleAuthOptions
)
```

### Example content of Google service accounts credentials JSON file
```json
{
  "type": "service_account",
  "project_id": "your-project-id",
  "private_key_id": "01234567890",
  "private_key": "-----BEGIN PRIVATE KEY-----YOUR PRIVATE KEY-----END PRIVATE KEY-----",
  "client_email": "service-acct@<your-poject-id>.iam.gserviceaccount.com",
  "client_id": "01234567890",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/service-acct%40your-service-account-name.iam.gserviceaccount.com"
}
```
