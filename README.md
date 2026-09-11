1. Push this repo to GitHub.
2. Create a new Web Service on Render pointing to this repo.
3. Set the `STRIPE_SECRET_KEY` environment variable in Render's dashboard.
4. Render will run `npm start`, which launches the Express server via `app.listen()`.

Firebase Cloud Functions (alternative):

1. Configure `firebase.json` and Firebase CLI.
2. Deploy with `firebase deploy --only functions`.
3. The same `index.js` exports the app as `exports.api` for this mode.

## Project Structure

```
amazon-clone-backend/
├── index.js        # Express app + dual-mode export (Functions / standalone)
├── firebase.json    # Firebase Functions config
├── package.json
└── .env             # Stripe secret key (gitignored)
```

## Related

- Frontend: [amazon-clone-frontend](https://github.com/hailemichaeltesfsye-hue/amazon-clone-frontend) — React app (Firebase Auth/Firestore, Stripe checkout UI)
- Netflix Clone: [Netflix_Clone_2026A](https://github.com/hailemichaeltesfsye-hue/Netflix_Clone_2026A) — React app (Firebase, TMDB API)

## Author

Hailemichael Tesfaye Mekuria [LinkedIn](https://www.linkedin.com/in/hailemichael-tesfaye-2b7114401/) · [GitHub](https://github.com/hailemichaeltesfsye-hue)
