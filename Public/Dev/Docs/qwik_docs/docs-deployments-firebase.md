# https://qwik.dev/docs/deployments/firebase/

[Original link](https://qwik.dev/docs/deployments/firebase/)

# Firebase Adapter

Qwik City Firebase Adapter allows you to connect Qwik City to Firebase.

## Installation

To integrate the firebase adapter, use the add command:

```
pnpm run qwik add firebase
```

```
npm run qwik add firebase
```

```
yarn run qwik add firebase
```

```
bun run qwik add firebase
```

The adapter will add a new vite.config.ts within the adapters/ directory, and a new entry file will be created, such as:

```
└── adapters/
    └── firebase
        └── vite.config.ts
└── src/
    └── entry-firebase.tsx
```

Additionally, within the package.json, the build.server and serve scripts will be updated.

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

## Deploy to Firebase

Before deploy you need to setup your Firebase Credentials and add a Firebase project to the repository using these commands.

```
firebase login
firebase use --add
pnpm run deploy
```

```
firebase login
firebase use --add
npm run deploy
```

```
firebase login
firebase use --add
yarn run deploy
```

```
firebase login
firebase use --add
bun run deploy
```

Done!

### Contributors

Thanks to all the contributors who have helped make this documentation better!
