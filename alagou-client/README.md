<h1 align="center">
  Alagou Client
</h1>

<p align="center">
 An app to that shows floods on the map and let the user register them.
</p>

<a align="center" href="./CHANGELOG.md">
  <img src="https://img.shields.io/badge/version-0.0.1-blue" />
</a>

## TOC

- [Workspace](#workspace)
- [Configuration](#configuration)
- [Building for production](#building-for-production)
- [Deep Linking](#deep-linking)

## Workspace

- Visual Studio Code 1.45.1

  - VSCode extensions:

    - Prettier - Code formatter 4.7.0
    - Eslint 2.1.5
    - VSCode MDX 0.1.4

  - VSCode settings:

  ```sh
  {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": false
    },
    "javascript.validate.enable": false,
    "eslint.validate": ["markdown", "md", "mdx"],
    "prettier.requireConfig": true,
  }
  ```

## Configuration

1. **Install these packages/applications (prefer the listed versions):**

- Node 12.18.2
- Yarn 1.21.1
- React Native CLI Quickstart (<https://reactnative.dev/docs/0.61/getting-started>)
  - Android Studio
  - JDK8
  - Watchman
  - Android Emulator - Pixel 2 API 30

2. **Install all dependencies with yarn (not npm!!)**

```sh
yarn
```

3. **Create a .env and a .env.production file with the respective required variables:**

For development:

```sh
API_ADDRESS=
GOOGLE_MAPS_APIKEY=
WEATHER_API_KEY=
```

For production

```sh
API_ADDRESS=
GOOGLE_MAPS_APIKEY=
WEATHER_API_KEY=
```

Important notes:

- If the variables don't update on changing, open metro with 'yarn start --reset-cache'.
- HTTP requests are blocked by android/ios by default. A possible workaround is to use the React Native Debugger with the Network Inspector turned on. You can also use HTTPS locally with the ngrok library on the server side of this app with the command 'yarn tunnel'.

3. **Change YOUR_API_KEY to your Google Maps API Key in AndroidManifest.xml (Android/app/main)**

```bash
  <meta-data
android:name="com.google.android.geo.API_KEY"
android:value="YOUR_API_KEY" />
```

4. **Create a signing key and set it and the Google Places API Key on gradle.properties**

- Generate a private signing key

```bash
yarn android:key
```

- Change the 'android/gradle.properties' with the key password

```bash
MYAPP_UPLOAD_STORE_FILE=
MYAPP_UPLOAD_KEY_ALIAS=
MYAPP_UPLOAD_STORE_PASSWORD=
MYAPP_UPLOAD_KEY_PASSWORD=
RNGP_ANDROID_API_KEY=
```

Important notes:

- You need to rebuild the app with 'yarn android:dev'.
- You should restrict the api key usage on Google Cloud Console with this signing key and app name.

5. **Start the app on android with**

```sh
yarn android:dev
```

6. **Commands**

```bash
# Installs all dependendies
$ yarn

# Starts metro server
$ yarn start

# Installs the android developer build (needs metro server to be active) (you need to unistall the prod app before trying to install this)
$ yarn android:dev

# Installs the android release build (needs to run android:build first) (you need to unistall the dev app before trying to install this)
$ yarn android:prod

# Builds a .apk file to be installed manually (needs a valid private signing key)
$ yarn android:build:apk

# Builds a .aab file used to be published in play store (needs a valid private signing key)
$ yarn android:build:aab

# Generate a private signing key
$ yarn android:key

# Install the ios developer build (currently not supported, because I'm missing a mac. It will need some fixes)
$ yarn ios:dev

# Checks Eslint errors
$ yarn lint

# Formats all files with prettier
$ yarn format

# Checks if all files are formatted with prettier
$ yarn check-format

# Checks typescript errors
$ yarn check-types

# Commits with karma interface
$ yarn commit
```

## Building for production

1. **Change the version code in android/app/build.gradle.**

2. **For android**

- Generate the build with:

```bash
yarn android:build:apk
```

3. **For ios**

Currently not supported, because I'm missing a mac. It will need some fixes.

# Deep Linking

Test it with npx uri-scheme open <schemeName>://<Route>/<Param>/<Param>/... --android

SchemeName is defined in AndroidManifest.xml
Route is defined in routes
Param is defined in routes

Example: npx uri-scheme open alagou://ResetPassword/123 --android
