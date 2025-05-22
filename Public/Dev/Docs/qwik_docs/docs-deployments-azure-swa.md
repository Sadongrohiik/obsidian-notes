# https://qwik.dev/docs/deployments/azure-swa/

[Original link](https://qwik.dev/docs/deployments/azure-swa/)

# Azure Static Web Apps Middleware

Qwik City Azure Static Web Apps middleware allows you to connect Qwik City to Azure Static Web Apps.

## Installation

To integrate the azure-swa adapter, use the add command:

```
pnpm run qwik add azure-swa
```

```
npm run qwik add azure-swa
```

```
yarn run qwik add azure-swa
```

```
bun run qwik add azure-swa
```

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── azure-swa/
        └── vite.config.ts
└── src/
    └── entry.azure-swa.tsx
```

Additionally, within the package.json, the build.server and deploy scripts will be updated.

## Production build

To build the application for production, use the build command, this command will automatically run build.server and build.client:

```
pnpm run build
```

```
npm run build
```

```
yarn run build
```

```
bun run build
```

## Deploy to Azure

After installing the integration the project is ready to be deployed to Azure Static Web Apps.

There are three ways to deploy:

Deploy with Static Web Apps CLI

You can deploy your application from your local environment with:

```
pnpm dlx swa deploy
```

```
npx swa deploy
```

```
yarn dlx swa deploy
```

```
bunx swa deploy
```

This will start a wizard which will guide you through login and deployment to Azure.

Deploy from GitHub

You can deploy your application via GitHub. Create a Git repository, commit all your code and then publish your branch to GitHub.

Create an Azure Static Webapp via the Azure Portal and choose the GitHub repository in the deployment details. When prompted for the build details choose "Custom" and set the following values:

This setup will establish a GitHub workflow in your repository. With this workflow, your application will automatically deploy whenever changes are pushed or merged into the main branch.

The resulting workflow file has to be adapted by adding the following to the "Repository/Build Configurations" block:

```
skip_api_build: true
```

Checkout Azure Static Web Apps quickstart for more information.

Deploy from any CI system

You can deploy to Azure Static Web Apps using any CI system. Set your Azure SWA deployment token as the SWA_CLI_DEPLOYMENT_TOKEN environment variable. Once that's done, you can run the following command in your pipeline:

```
swa deploy ./dist --api-location ./azure-functions --env production
```

Notice, that you will need an Azure account in order to complete this step!

### Contributors

Thanks to all the contributors who have helped make this documentation better!
