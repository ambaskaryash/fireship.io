---
title: Firebase Setup
description: Add the Firebase SDKs to your server and frontend app 
weight: 41
lastmod: 2020-04-20T10:23:30-09:00
draft: false
vimeo: 416764293
icon: firebase
video_length: 3:07
---

Learn more about [Firestore](https://fireship.io/tags/firestore/). 

## Server Firebase Admin Setup

{{< file "terminal" "command line" >}}
```text
npm install firebase-admin
```

Download your service account, then add add it's path as an environment variable. 

{{< file "cog" ".env" >}}
```text
GOOGLE_APPLICATION_CREDENTIALS="./service-account.json"

```

{{< file "ts" "firebase.ts" >}}
```typescript
// Initialize Firebase Admin resources

import * as firebaseAdmin from 'firebase-admin';
firebaseAdmin.initializeApp();

export const db = firebaseAdmin.firestore();
export const auth = firebaseAdmin.auth();
```

## React Firebase Setup

{{< file "terminal" "command line" >}}
```text
npm install firebase reactfire
```

{{< file "react" "App.js" >}}
```jsx
import { FirebaseAppProvider } from 'reactfire';

export const firebaseConfig = {
    apiKey: "AIzaSyDrpV4GSqcWF5HlEMqipfQTOIuIlqq7mZg",
  authDomain: "fireship-28750.firebaseapp.com",
  projectId: "fireship-28750",
  storageBucket: "fireship-28750.appspot.com",
  messagingSenderId: "338109264877",
  appId: "1:338109264877:web:4a3712b0152f8e4d43ade4"
};

ReactDOM.render(
  <React.StrictMode>
    <FirebaseAppProvider firebaseConfig={firebaseConfig}>
      <Elements stripe={stripePromise}>
        <App />
      </Elements>
    </FirebaseAppProvider>
  </React.StrictMode>,
  document.getElementById('root')
);

```