# Amazon Clone — Backend

Express API powering the payment flow for the [Amazon Clone](https://github.com/hailemichaeltesfsye-hue/amazon-clone-frontend) frontend. Handles Stripe payment intents and integrates with Firebase for order storage on the client side.

## Stack

- **Node.js + Express** — REST API server
- **Stripe** (test mode) — payment intent creation
- **Firebase** (Firestore) — used by the frontend for order persistence
- Deployable in two modes: **Firebase Cloud Functions** or **standalone server** (Render/Docker)

## Features

- `POST /payment/create` — creates a Stripe PaymentIntent for a given amount
- Dual-mode export: runs as a Firebase Cloud Function (`exports.api`) **or** as a standalone Express server (`app.listen()`) when run directly — enables deployment on platforms like Render without requiring Firebase's paid Blaze plan
- CORS-enabled for requests from the React frontend

## Getting Started

### Prerequisites

- Node.js (LTS recommended)
- A Stripe account with a test secret key
- (Optional) Firebase project, if deploying via Cloud Functions

### Installation

```bash
git clone https://github.com/hailemichaeltesfsye-hue/amazon-clone-backend.git
cd amazon-clone-backend
npm install
```

### Environment Variables

Create a `.env` file in the project root:

```
STRIPE_SECRET_KEY=your_stripe_secret_key
```

> `.env` is gitignored — never commit real keys.

### Running Locally (standalone mode)

```bash
npm start
```

The server starts on the configured port (default `8080`) and exposes the payment endpoint at:

```
http://localhost:8080/payment/create
```

### Deploying

**Render (standalone server):**
1. Push this repo to GitHub.
2. Create a new Web Service on Render pointing to this repo.
3. Set the `STRIPE_SECRET_KEY` environment variable in Render's dashboard.
4. Render will run `npm start`, which launches the Express server via `app.listen()`.

**Firebase Cloud Functions (alternative):**
1. Configure `firebase.json` and Firebase CLI.
2. Deploy with `firebase deploy --only functions`.
3. The same `index.js` exports the app as `exports.api` for this mode.

## Project Structure

```
amazon-clone-backend/
├── index.js          # Express app + dual-mode export (Functions / standalone)
├── firebase.json      # Firebase Functions config
├── package.json
└── .env               # Stripe secret key (gitignored)
```

## Related

- Frontend: [amazon-clone-frontend](https://github.com/hailemichaeltesfsye-hue/amazon-clone-frontend) — React app (Firebase Auth/Firestore, Stripe checkout UI)

## Author

**Hailemichael Tesfaye Mekuria**
[LinkedIn](https://www.linkedin.com/in/hailemichael-tesfaye-2b7114401/) · [GitHub](https://github.com/hailemichaeltesfsye-hue)
