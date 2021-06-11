# Fake REST API NodeJS

Get a full fake REST API with **zero coding** in **less than 30 seconds** ([NodeJS](https://nodejs.org/en/) + [JSON Server](https://github.com/typicode/json-server) + [JSON Webtoken](https://github.com/auth0/node-jsonwebtoken)).

Support JWT Bearer authentication:

- Register user with username & password or email & password.

- Login with registered users.

- Protect API by resource and request methods.

- Upload files.

## Getting started

### 1. Clone this repository

```bash
git clone https://github.com/robinhuy/fake-rest-api-nodejs.git
```

or fork to your account and clone the forked repo

### 2. Install dependencies

```bash
cd fake-rest-api-nodejs
npm install
```

or if you using yarn

```bash
cd fake-rest-api-nodejs
yarn install
```

### 3. Run server

- Production mode:

  ```bash
  npm start
  ```

  or

  ```bash
  yarn start
  ```

- Development mode (auto reload server when editing using [nodemon](https://github.com/remy/nodemon)):

  ```bash
  npm run dev
  ```

  or

  ```bash
  yarn dev
  ```

- The server will run on `http://localhost:3000`. You can test with public endpoint: `http://localhost:3000/products` (GET method).

## Modify your data

All the data was placed in `database.json`. Edit it to suit your purpose.

You can use [https://mockaroo.com/](https://mockaroo.com/) to mock data, and publish your code to [https://heroku.com/](https://heroku.com/) or similar hosting to get a Public API.

**Note**:

- To protect resources, decleare resources and protected methods in `database.json`:

  ```json
  "protected_resources": {
    "users": ["GET", "POST", "PUT", "PATCH", "DELETE"],
    "products": ["POST", "PUT", "PATCH", "DELETE"]
  }
  ```

- To register new user, using endpoint `/register`, method `POST`, request type `application/json`. Body request like `users` resources:

- To login, using endpoint `/login`, method `POST`, request type `application/json`. Body request like this:

  ```json
  {
    "username": "admin",
    "password": "admin"
  }
  ```

  or

  ```json
  {
    "email": "admin@gmail.com",
    "password": "admin"
  }
  ```

- To upload single file, using endpoint `/upload-file`, method `POST`, request type `form-data`, field `file`. Uploaded file stored in `/public/uploads/`.

- To upload multiple files, using endpoint `/upload-files`, method `POST`, request type `form-data`, field `files`. Uploaded files stored in `/public/uploads/`.

- Change default port, database file, jwt secret or jwt token expires in `config.json`.

## Access & modify API

Please view detailed document in [https://github.com/typicode/json-server/blob/master/README.md#table-of-contents](https://github.com/typicode/json-server/blob/master/README.md#table-of-contents)

If you want to change logic of authentication or add more feature, please edit file `server.js` or `additional_routes.js`.
