# https://qwik.dev/docs/deployments/bun/

[Original link](https://qwik.dev/docs/deployments/bun/)

# Bun Middleware

Qwik City Bun middleware allows you to hook up Qwik City to a Bun server which uses the Bun Http API.

## Installation

To install bun on Linux, OSX or WSL run the following command in your terminal

```
curl -fsSL https://bun.sh/install | bash
```

For other platforms or if you run into issues with installation, up to date bun installation instructions can be found on the bun website.

To integrate the bun adapter, use the add command:

```
bun run qwik add bun
```

## Production build

To build the application for production, use the build command, this command will automatically run bun run build.server and bun run build.client:

```
bun run build
```

## Serve

To start the Bun server after a build:

```
bun run serve
```

## Production deploy

Since you are choosing Bun, here you are in your own, after running bun run build:

### Contributors

Thanks to all the contributors who have helped make this documentation better!
