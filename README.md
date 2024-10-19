# Google JWT SA ✨

Gets a Google Auth Token (OAuth 2.0) for Google Workspace Service Accounts. Used
for server to server applications and domain wide delegation.

### Usage

```ts
import {
  getToken,
  GoogleAuth,
} from "https://deno.land/x/googlejwtsa@{version}/mod.ts";

const googleServiceAccountCredentials = await Deno.readTextFile(
  filepath,
);

const googleAuthOptions = {
  scope: ["<Google API Endpoint URL>"], // array of Google's endpoint URLs
  delegationSubject: "admin@yourdomain.com", // optional subject for domain delegation
};

const token = await getToken(
  googleServiceAccountCredentials,
  googleAuthOptions,
);


const response = await fetch("<Google API Endpoint URL>", {
  method: 'POST',
  body: '<body>',
  headers: {
    'Content-Type': 'application/json',
    'accept': 'application/json',
    'Authorization': `Bearer ${token.access_token}` // or token.id_token
  },
});
```

### Example content of Google service accounts credentials JSON file. Get this from Google's admin console.

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
