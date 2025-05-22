# https://qwik.dev/docs/guides/capacitor/

[Original link](https://qwik.dev/docs/guides/capacitor/)

# Qwik for iOS and Android

## Modernizing Mobile Development with a Hybrid Approach

Traditionally, building native mobile applications meant managing two separate codebases: Swift/Objective-C for iOS and Kotlin/Java for Android. While this approach offers deep integration with each platform, it comes with significant drawbacks, including increased development time, higher costs, and doubled maintenance efforts for every feature or bug fix.

This new hybrid approach combines Qwik's performance-optimized framework with Capacitor's native runtime and Capawesome's rich plugin ecosystem, enabling developers to build high-performance mobile applications from a single TypeScript codebase. This architecture bridges the gap between web and native development, allowing:

## How It Works

The architecture combines three complementary technologies—Qwik, Capacitor, and a robust plugin ecosystem—to create a streamlined, high-performance hybrid mobile development platform. This approach prioritizes speed, native integration, and efficient resource usage, ensuring a smooth experience for both developers and end-users.

### 1. Qwik Static Site Generation (SSG)

At the core of this stack, your application is built as a Qwik Static Site. Qwik's Static Site Generation (SSG) approach ensures that most of the application is pre-rendered at build time, resulting in lightweight assets that are optimized for mobile devices.

Why Static for Capacitor?

Key Benefits of Qwik SSG:

Together, Qwik SSG and Capacitor enable an architecture where your app's web content behaves like native assets, loaded directly from the device with no dependency on external servers.

### 2. Capacitor Integration

Capacitor acts as the bridge between your Qwik-generated static assets and native mobile APIs. It wraps your app in a native runtime, making it possible to access native device capabilities directly from your TypeScript code.

Why Capacitor is Essential:

Key Benefits of Capacitor:

By using Capacitor, your static Qwik app becomes a self-contained mobile app that can interact with device hardware and APIs as if it were built natively. Please refer to the official Capacitor documentation for more information on how to use Capacitor.

### 3. Accessing Native Features

Capacitor enables your Qwik app to interact with native device features through an extensive ecosystem of plugins. These plugins act as modular bridges that translate JavaScript API calls into native commands, allowing seamless access to hardware and platform-specific functionality like the camera, GPS, or file system.

#### Capacitor Plugins:

Capacitor Plugins can be found here.

#### Capawesome Plugins:

Capawesome expands Capacitor’s functionality with a collection of plugins designed to address advanced and specialized use cases not always covered by Capacitor's core plugin set. Two notable examples demonstrate its unique value:

Live Updates: Enables over-the-air updates for the app's web layer, allowing developers to deliver bug fixes, improvements, and new features without requiring users to download a new version from the app store. This reduces release cycle friction and ensures users always have the latest experience.

Bluetooth Low Energy (BLE): Offers reliable APIs for communicating with Bluetooth Low Energy peripherals, supporting secure and efficient interactions with devices such as fitness trackers, medical sensors, and smart IoT equipment.

Capawesome plugins are built with a TypeScript-first philosophy, ensuring strong type safety, modern development standards, and seamless integration with development tools and workflows. This focus results in plugins that are easier to maintain, debug, and scale across projects.

Many more Capawesome Plugins can be found here.

#### Cordova Plugins:

Cordova Plugins can be found here.

## Prerequisites and Initial Setup

### Required Tools

Please refer to each platform's official documentation for installation instructions and application build process.

### Environment Setup

Create a Qwik Project
Start by creating a new Qwik project using the CLI:

```
pnpm create qwik@latest
```

Add the Static Adapter
To prepare your Qwik app for static site generation (SSG), install the static adapter:

```
pnpm run qwik add static
```

This step ensures your app generates pre-rendered static files suitable for Capacitor.

Add Capacitor to Your Qwik Project
Install Capacitor dependencies and initialize Capacitor:

```
pnpm i @capacitor/cli @capacitor/core
npx cap init
```

Configure Capacitor
Your capacitor.config.ts file should looks something like this:

```
import type { CapacitorConfig } from '@capacitor/cli';
 
 const config: CapacitorConfig = {
   appId: 'com.example.app',
   appName: 'my-qwik-empty-starter',
   webDir: 'dist',
   server: {
     iosScheme: 'capacitor',
     androidScheme: 'https'
   }
 };
 
 export default config;
```

Install Platform-Specific Dependencies
Add support for iOS and Android platforms:

```
pnpm i @capacitor/ios @capacitor/android
```

Initialize Native Platforms
Create the native project files:

```
npx cap add ios
npx cap add android
```

## Development Workflow

### Building and Running

In this section, we’ll walk through the process of creating a production-ready build of your Qwik application, syncing it with native platforms using Capacitor, and deploying it to an iOS simulator or Android emulator. This workflow ensures that your app is packaged with optimized static assets, making it ready for testing and deployment on mobile devices. Whether you're verifying functionality, refining the user experience, or preparing for final distribution, running the app in a native simulator or emulator is an essential step in validating its performance and behavior across platforms.

```
pnpm run build
```

```
npx cap sync
```

```
npx cap run ios     # Runs the app in an iOS simulator
npx cap run android # Runs the app in an Android emulator
```

Alternatively you can open native IDEs:

```
npx cap open ios     # Opens Xcode
npx cap open android # Opens Android Studio
```

## How to Use Native Functionality with Plugins

The Device Plugin is a straightforward example of how to integrate native functionality into your Qwik app using Capacitor. This plugin allows you to access key device-specific information, such as the model, operating system, and OS version. This data can be valuable for debugging, adapting your app's behavior based on the device's capabilities, or collecting insights for analytics. Importantly, the Device plugin works seamlessly in both iOS simulators and Android emulators, making it an ideal choice for testing native integration without requiring additional configuration.

### Install the Device Plugin

```
pnpm i @capacitor/device
```

```
plugins: {
  Device: {
    // No configuration required
  },
},
```

```
import { component$, useSignal, useVisibleTask$ } from '@builder.io/qwik';
import { Device } from '@capacitor/device';
 
export const DeviceInfoComponent = component$(() => {
  const deviceInfo = useSignal<string | null>(null);
 
  useVisibleTask$(async () => {
    const info = await Device.getInfo();
    deviceInfo.value = `Model: ${info.model}, OS: ${info.operatingSystem}, Version: ${info.osVersion}`;
  });
 
  return (
    <div style={{ paddingTop: "40px" }}>
      <h2>Device Information</h2>
      {deviceInfo.value ? (
        <p>{deviceInfo.value}</p>
      ) : (
        <p>Loading device information...</p>
      )}
    </div>
  );
});
```

You will need to update the native platforms to ensure that the plugin is properly integrated into your app. This step ensures that the native code is available for the Qwik app.

NOTE: As of the time of writing this guide, a bug exists in XCode that requires you to delete the iOS app before redeploying.

```
npx cap sync
npx cap run ios     # Runs the app in an iOS simulator
npx cap run android # Runs the app in an Android emulator
```

## 📚 Over-the-Air Updates with Capawesome

This is a highly simplified example of how to self-host a live update from your local system. To implement a robust OTA update system please follow the guides provided at Capawesome.

```
pnpm i @capawesome/capacitor-live-update
```

```
plugins: {
    ...
    LiveUpdate: {
      appId: "YOUR_APP_ID",
      // publicKey:
      //   "-----BEGIN PUBLIC KEY-----\nYOUR_PUBLIC_KEY\n-----END PUBLIC KEY-----",
    },
  },
```

```
import {
  $,
  component$,
  useComputed$,
  useSignal,
  useVisibleTask$,
} from "@builder.io/qwik";
import type { DocumentHead } from "@builder.io/qwik-city";
import { LiveUpdate } from "@capawesome/capacitor-live-update";
 
const VERSION = "1.0.0";
const OTA_SERVER_URL = "http://YOUR_IP:8000";
const wait = () => new Promise((resolve) => setTimeout(resolve, 1000));
 
export default component$(() => {
  const version = useSignal<string>(VERSION);
  const updateStatus = useSignal<string | null>(null);
  const otaUrl = useComputed$(() => `${OTA_SERVER_URL}/${version.value}.zip`);
 
  const handleUpdate = $(async () => {
    try {
      updateStatus.value = `Checking for existing bundle...`;
      console.log(updateStatus.value);
      await wait();
 
      const { bundleIds } = await LiveUpdate.getBundles();
      const bundleExists = bundleIds.includes(version.value);
 
      if (bundleExists) {
        updateStatus.value = `Bundle ${version.value} already exists. Switching to it...`;
        console.log(updateStatus.value);
        await wait();
 
        await LiveUpdate.setNextBundle({ bundleId: version.value });
        await LiveUpdate.reload();
 
        updateStatus.value = `Switched to existing bundle ${version.value}!`;
        console.log(updateStatus.value);
        await wait();
      } else {
        updateStatus.value = `Downloading update from ${otaUrl.value}...`;
        console.log(updateStatus.value);
        await wait();
 
        await LiveUpdate.downloadBundle({
          url: otaUrl.value,
          bundleId: version.value,
        });
 
        updateStatus.value = "Applying update...";
        console.log(updateStatus.value);
        await wait();
 
        await LiveUpdate.setNextBundle({ bundleId: version.value });
        await LiveUpdate.reload();
 
        updateStatus.value = "Update applied successfully!";
        console.log(updateStatus.value);
        await wait();
      }
    } catch (error) {
      updateStatus.value = `Update to ${otaUrl.value} failed. Error: ${
        error instanceof Error ? error.message : "Unknown error"
      }`;
      console.error(updateStatus.value);
      await wait();
    }
  });
 
  useVisibleTask$(async () => {
    try {
      updateStatus.value = "App ready";
      console.log(updateStatus.value);
      await wait();
 
      LiveUpdate.ready();
    } catch (error) {
      (updateStatus.value = "Error notifying app readiness:"), error;
      console.error(updateStatus.value);
      await wait();
    }
  });
 
  return (
    <div style={{ padding: "40px" }}>
      <h2>OTA Update</h2>
      <h3>Current Version: {VERSION}</h3>
      <p>Enter the version you want to update to and click the button below.</p>
 
      <div style={{ marginBottom: "20px" }}>
        <label>
          Version:
          <input
            value={version.value}
            onInput$={(event) =>
              (version.value = (event.target as HTMLInputElement).value)
            }
            style={{
              marginLeft: "10px",
              padding: "8px",
              fontSize: "14px",
              borderRadius: "5px",
              border: "1px solid #ccc",
            }}
          />
        </label>
      </div>
 
      <button
        onClick$={handleUpdate}
        style={{
          marginTop: "10px",
          padding: "10px 20px",
          fontSize: "14px",
          cursor: "pointer",
          borderRadius: "5px",
          border: "none",
          backgroundColor: "#0078D4",
          color: "#fff",
        }}
      >
        Update Now
      </button>
 
      {updateStatus.value && (
        <p style={{ marginTop: "20px" }}>{updateStatus.value}</p>
      )}
    </div>
  );
});
 
export const head: DocumentHead = {
  title: "Dynamic OTA Update with Capawesome",
  meta: [
    {
      name: "description",
      content: "Qwik app with OTA updates.",
    },
  ],
};
```

Build and deploy the app to your device.

```
pnpm run build
npx cap sync
npx cap run ios     # Runs the app in an iOS simulator
npx cap run android # Runs the app in an Android emulator
```

Update the version number in the index.tsx file and zip it with the same version number (i.e. 1.0.1.zip). You can build multiple versions and switch between them.

```
mkdir -p ota_bundles # Only required the first time
pnpm run build
zip -r ota_bundles/VERSION.zip dist/*
```

```
npx serve ota_bundles -l 8000
```

Once the app is updated, the new version will be used across app launches. You can repeat step 5 to create a new bundles.

#### Capawesome Cloud

If you are using Capawesome Cloud, you can use the Live Update plugin to update your app without having to build and host a new version of the app. This is a great option for production environments.

### Live Development

Live development is a critical part of building modern hybrid mobile applications, allowing developers to make changes to their code and see the results in real-time on a connected device or simulator. With Capacitor’s live reload feature, you can bridge the gap between rapid web development workflows and native mobile deployment. Instead of waiting through lengthy build and redeployment cycles, live development enables instant feedback, making it easier to fine-tune UI elements, test native functionality, and troubleshoot platform-specific behaviors. This approach reduces development friction, accelerates iteration, and fosters a smoother experience when building, testing, and refining Qwik-powered mobile apps.

```
server: {
  ...
  host: true, // Enables access from the local network
 }
```

```
const config: CapacitorConfig = {
  ...
  server: {
    url: 'http://YOUR_IP:5172',
    cleartext: true
  }
};
```

```
npx cap run ios
npx cap run android
```

```
pnpm run dev
```

NOTE: After you run the dev server, you will need to restart the native IDEs to see the changes.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
