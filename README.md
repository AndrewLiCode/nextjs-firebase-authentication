# Next.js Starter

**Server-Side User Management with**

  - Sign In
  - Sign Up
  - Sign Out
  - Password Change
  - Password Reset

**Client and Server-Side Protected Routes with**

- Next.js Authorization and Firebase Session

**Payment with**

- Stripe
- PayPal

**Styling with**

- [Ant Design](https://ant.design/)
- Styled Components
- Page Transitions

**Type Support with**

- TypeScript

**Tested Code Base with**

- [Jest](https://jestjs.io/)
- [React Testing Library](https://github.com/testing-library/react-testing-library)
- [Apollo Mocks](https://www.apollographql.com/docs/react/development-testing/testing/)

**Environment Variables with**

- [Dotenv](https://github.com/motdotla/dotenv)

**Absolute Imports with**

- Babel Module Resolver

## Installation

- See other installation instructions below ...
- `npm install`
- `npm run dev`
- Visit http://localhost:3000/

### .env file

Create a _.env_ file. If using git, add it to your _.gitignore_ file.

Values may differ for development and production:

```
BASE_URL=http://localhost:3000

FIREBASE_API_KEY=apiKey
FIREBASE_AUTH_DOMAIN=authDomain
FIREBASE_DATABASE_URL=databaseURL
FIREBASE_PROJECT_ID=projectID
FIREBASE_STORAGE_BUCKET=storageBucket
FIREBASE_MESSAGING_SENDER_ID=messagingSenderId
FIREBASE_APP_ID=appId

PAYPAL_CLIENT_ID=xxx
PAYPAL_CLIENT_SECRET=xxx

STRIPE_CLIENT_ID=pk_test_xxx
STRIPE_CLIENT_SECRET=sk_test_xxx
STRIPE_WEBHOOK_SECRET=xxx

COUPON_SALT=SOMETHING TO BE REPLACED BEFORE HTTING THE COUPON URL
COUPON_URL=URL TO GET A CONVERSION FACTOR
FIREBASE_ADMIN_UID=SOME FIREBASE USER'S UID
```

- [FIREBASE](https://firebase.google.com/)
  - Activate Email/Password Sign-In Method for your Firebase Project
- [PAYPAL](https://developer.paypal.com/)
  - [Checkout](https://developer.paypal.com/docs/checkout/)
- [STRIPE](https://stripe.com/)
  - [Checkout](https://stripe.com/docs/payments/checkout/one-time)
  - [Webhook](https://stripe.com/docs/payments/checkout/fulfillment#webhooks)

### .firebaseServiceAccountKey.json file

Visit [here](https://firebase.google.com/docs/admin/setup/#initialize-sdk) for Firebase Admin SDK and generate a _firebaseServiceAccountKey.json_ file from there which should be in your project's root folder. If using git, add it to your _.gitignore_ file.

### Admin Account

If you want to have an account with Firebase admin claims, create this Firebase account first via UI, then set the user account's `uid` in _.env_ with `FIREBASE_ADMIN_UID`, and restart your sercer.

### Stripe CLI for Webhook in Development Mode

[Stripe CLI](https://stripe.com/docs/stripe-cli)

```
stripe login
# follow instructions
stripe listen --forward-to localhost:3000/api/stripe-webhook
# copy and paste secret
```

The `secret` can be used in _.env_:

```
STRIPE_WEBHOOK_SECRET=secret
```

Then fake a request with Stripe CLI `stripe payment_intents create --amount=100 --currency=usd` will work. Make sure the application is running too. Or use the web application's Stripe Checkout feature for real.
