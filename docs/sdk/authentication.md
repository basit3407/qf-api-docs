---
id: authentication
title: "🔑 Authentication"
sidebar_label: Authentication
---

The SDK uses the OAuth2 **Client Credentials** flow behind the scenes. Once you call `configure` with your `clientId` and `clientSecret`, every request automatically obtains and refreshes an access token.

## How it works

1. The SDK requests a token from `https://oauth2.quran.foundation/oauth2/token` using your credentials.
2. Tokens are cached until 30 seconds before expiry.
3. All API calls include the `x-auth-token` and `x-client-id` headers for you.

You generally do not need to handle tokens manually. If you wish to override the fetch implementation (for example in React Native), pass a custom `fetchFn` during configuration:

```javascript
import { configure } from '@quranjs/api';
import fetch from 'cross-fetch';

configure({
  clientId: 'YOUR_CLIENT_ID',
  clientSecret: 'YOUR_CLIENT_SECRET',
  fetchFn: fetch,
});
```

For details on the OAuth2 endpoints themselves, see the [OAuth2 API reference](https://api-docs.quran.foundation/docs/oauth2_apis_versioned/token).
