# https://qwik.dev/docs/deployments/gcp-cloud-run/

[Original link](https://qwik.dev/docs/deployments/gcp-cloud-run/)

# Google Cloud Run Middleware

Qwik City Cloud Run middleware allows you to run a Qwik City app on Google Cloud Run

## Installation

To integrate the Cloud Run adapter, use the add command:

```
pnpm run qwik add cloud-run
```

```
npm run qwik add cloud-run
```

```
yarn run qwik add cloud-run
```

```
bun run qwik add cloud-run
```

## Production deploy

To deploy your app, you need to:

Have a Google Cloud account

Install the gcloud CLI

If you don't have gcloud, follow Google Cloud's official documentation.

Authenticate with the gcloud CLI

To authenticate the gcloud CLI, run this command:

```
gcloud auth login
```

Grant the SDK access to the account you created in step 1.

Change the name of the deploy script

Update the name of your Cloud Run app in the deploy script in your package.json.

```
"deploy": "gcloud run deploy my-cloud-run-app --source ."
```

Run deploy script

Deploy to Google Cloud Run with:

```
pnpm run deploy
```

```
npm run deploy
```

```
yarn run deploy
```

```
bun run deploy
```

### Contributors

Thanks to all the contributors who have helped make this documentation better!
