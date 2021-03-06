<h1 align="center">
  Alagou Server
</h1>

<p align="center">
  A server for the server client project.
</p>

<a align="center" href="./CHANGELOG.md">
  <img src="https://img.shields.io/badge/version-0.0.1-blue" />
</a>

## TOC

- [Workspace](#workspace)
- [Configuration](#configuration)

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
- MongoDB (Currently using MongoDB Cloud, but can be the local version)

2. **Create a .env file with the required variables:**

```sh
SECRET_KEY=
MONGO_URI=
CLOUDNAME=
CLOUDKEY=
CLOUDSECRET=
PORT=
NODEMAILER_EMAIL_ADRESS=
NODEMAILER_PASSWORD=
SERVER_URL=
EMAIL_PORT=
```

3. **Install all dependencies with yarn (not npm!!)**

```sh
yarn
```

4. **Start nodemon**

```sh
yarn dev
```

5. **Commands**

```bash
# Installs all dependendies
$ yarn

# Start the server for development
$ yarn dev

# Start the server for production
$ yarn start

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
