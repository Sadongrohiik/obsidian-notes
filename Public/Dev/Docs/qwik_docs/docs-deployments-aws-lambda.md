# https://qwik.dev/docs/deployments/aws-lambda/

[Original link](https://qwik.dev/docs/deployments/aws-lambda/)

# AWS Adapter

Qwik City AWS Adapter allows you to connect Qwik City to AWS Lambda.

## Installation

To integrate the aws-lambda adapter, use the add command:

```
pnpm run qwik add aws-lambda
```

```
npm run qwik add aws-lambda
```

```
yarn run qwik add aws-lambda
```

```
bun run qwik add aws-lambda
```

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── aws-lambda
        └── vite.config.ts
└── src/
    └── entry_aws-lambda.tsx
```

Additionally, within the package.json, the build.server and serverless:preview scripts will be updated.

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

## Deploy to AWS

Before deployment, you need to set up your AWS Credentials. Under the hood,
the adapter uses serverless.

```
serverless deploy
```

Done!

### Contributors

Thanks to all the contributors who have helped make this documentation better!
