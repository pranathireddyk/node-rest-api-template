# Node.js REST API starter

<img src="https://raw.githubusercontent.com/stackinflow/node-rest-api-starter/master/assets/banner-node-rest-api.png">

[![stackinflow](https://img.shields.io/badge/stackinflow-opensource-brightgreen)](https://stackinflow.github.io/) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/215290ffb548419bbff773ca8abcdb3d)](https://app.codacy.com/gh/stackinflow/node-rest-api-starter?utm_source=github.com&utm_medium=referral&utm_content=stackinflow/node-rest-api-starter&utm_campaign=Badge_Grade_Dashboard) [![Build Status](https://github.com/stackinflow/node-rest-api-starter/workflows/Mocha-Tests/badge.svg)](https://github.com/stackinflow/node-rest-api-starter/actions)

<a href="https://www.buymeacoffee.com/fayaz" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-violet.png" alt="Buy Me A Coffee" height="45px" width="180px" ></a>

This repository is a template to avoid rewriting all the basic authentication code for REST API's built with Express.js, MongoDB.

## Table of contents

1. [Why this template](#why-this-template)
2. [Project architecture & Directories Structure](#project-architecture-structrue)
3. [Tech stack](#tech-stack)
4. [Install and configure Node.js](#installation-of-nodejs)
5. [Mongodb Installation and Configuration](#mongodb-installation-configuration)
6. [Setup and Run the Project](#setup-and-run-the-project)
7. [Setup GitHub actions](#setup-gh-actions)
8. [Authors](#authors)
9. [Contributing](#contributing)

<!--
(#why-this-template)
-->
## Why this template

- This repository includes setup of all basic things required to start a MEAN/MERN stack backend
- Environments setup
- Connection to database(MongoDB)
- Admin routes for handling users
- Authentication - fully handled
- Social auth includes Facebook and Google OAuth2 authorization
- Provides clean structured code
- Mocha Tests to ensure API is working
- Email templates for account verification and password reset
- Token based email verification and OTP based password reset
- Body field validators

<!--
(#project-architecture-structrue)
-->
## Project architecture & Directories Structure

```
.
├── api
│   └── v1
│       ├── controllers
│       │   ├── auth.js
│       │   └── token.js
│       ├── middlewares
│       │   └── auth.js
│       ├── models
│       │   ├── auth.js
│       │   └── token.js
│       ├── routes
│       │   ├── admin
│       │   │   └── auth.js
│       │   └── auth.js
│       └── utils
│           ├── constants.js
│           ├── response.js
│           ├── send_email.js
│           ├── templates
│           │   └── verify_email.pug
│           └── validators.js
├── ASSET_LICENSES
├── core
│   ├── config.js
│   ├── db.js
│   ├── jwt.js
│   ├── print_env.js
│   └── server.js
├── index.js
├── keys
│   ├── private.pem
│   ├── private.pem.example
│   ├── privater.pem
│   ├── privater.pem.example
│   ├── public.pem
│   ├── public.pem.example
│   ├── publicr.pem
│   └── publicr.pem.example
├── LICENSE
├── node-rest-api-auth.postman_collection.json
├── package.json
├── package-lock.json
├── public
│   └── images
├── README.md
└── tests
    └── v1
        ├── auth.js
        └── test.js
```

<!--
(#tech-stack)
-->
## Tech stack

Node.js, MongoDB

### Dependencies

```
1. @hapi/joi: ^17.1.1
2. @sendgrid/mail: ^7.2.3
3. axios: ^0.19.2
4. bcryptjs: ^2.4.3
5. body-parser: ^1.19.0
6. cors: ^2.8.5
7. csurf: ^1.11.0
8. dotenv: ^8.2.0
9. express: ^4.17.1
10. express-brute: ^1.0.1
11. express-brute-memcached: 0.0.1
12. helmet: ^4.0.0
13. jsonwebtoken: ^8.5.1
14. mongoose: ^5.9.27
15. multer: ^1.4.2
16. nodemailer: ^6.4.11
17. otp-generator: ^1.1.0
18. pug: ^3.0.0
19. socket.io: ^2.3.0
```

### Dev dependencies

```
1. chai: ^4.2.0
2. chai-http: ^4.3.0
3. eslint: ^7.6.0
4. eslint-config-prettier: ^6.11.0
5. mocha: ^8.1.1
6. nodemon: ^2.0.4
7. prettier: ^2.0.5
```

### Tests

Tests are written using Mocha and Chai

### CI/CD

Not implemented yet


## Project setup

<!--
(#installation-of-nodejs)
-->

## Installation of Node.js

First thing we need to do is to install **nodejs**, you can find the installation steps and archives from the official website [here](https://nodejs.org/en/). It is recommended to use the LTS version of node to avoid any kind of interruptions.

#### Install specific version using CURL

1. Install `curl`

```bash
sudo apt update
sudo apt upgrade
sudo apt install curl
```

2. Get `nodejs` PPA
   Switch to root directory

```bash
cd ~
```

```bash
curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
```

3. Run the script under sudo:

```bash
sudo bash nodesource_setup.sh
```

4. Install nodejs

```bash
sudo apt install nodejs
```

5. In order for some npm packages to work (those that require compiling code from source, for example), you will need to install the build-essential package:

```bash
sudo apt install build-essential
```

<!--
(#mongodb-installation-configuration)
-->

## Mongodb installation and configuration

In case you face any issues, refer official [docs](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)

#### Installing mongodb v4.2

a. Import the public key used by the package management system.

```bash
wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -
```

b. Create a list file for MongoDB

```bash
echo  "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```

c. Reload local package database.

```bash
sudo apt-get update
```

d. Install the MongoDB packages

```bash
sudo apt-get install -y mongod
```

e. Optional. Although you can specify any available version of MongoDB

```bash
echo  "mongodb-org hold" | sudo dpkg --set-selections
echo  "mongodb-org-server hold" | sudo dpkg --set-selections
echo  "mongodb-org-shell hold" | sudo dpkg --set-selections
echo  "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo  "mongodb-org-tools hold" | sudo dpkg --set-selections
```

#### Configure mongodb

a. Create a directory to store data

```bash
sudo mkdir /data
sudo mkdir /data/db
```

b. Grant required permissions

```bash
sudo chown -R `id -un` /data/db
```

#### Start mongodb services

```bash
# start mongodb service
sudo service mongod start
# Check status of the service
sudo service mongod status
```

#### Initialize MongoDB

```bash
sudo mongod
```

The above command will start a `MongoDB` instance running on your local machine. I will pick a port to run the database, possibly it will be `27017`, so your db will be hosted at

```js
mongodb://localhost:27017/
```

#### MongoDB shell

Here you can execute your db queries. Initialize the shell by following command

```bash
mongo
```

<!--
(#setup-and-run-the-project)
-->

## Setup and run the project

1. Install the required dependencies by the following command

```bash
npm install
```

2. Setup public & private keys for `Access` and `Refresh` tokens
   Open your terminal and type the below commands to create secure private key and extracting public key from the private key. We're using a 512 bit long key, as the length increases the size of jwt also increases.

Creating private key for access token

```bash
openssl genrsa -out private.pem 512
```

Expected output:

```
Generating RSA private key, 512 bit long modulus (2 primes)
....................................................+++++
.+++++
```

Extracting public key for access token

```bash
openssl rsa -in private.pem -outform PEM -pubout -out public.pem
```

Expected output:

```
writing RSA key
```

Creating private key for refresh token

```bash
openssl genrsa -out privater.pem 512
```

Expected output:

```
Generating RSA private key, 512 bit long modulus (2 primes)
....................................................+++++
.+++++
```

Extracting public key for refresh token

```bash
openssl rsa -in privater.pem -outform PEM -pubout -out publicr.pem
```

Expected output:

```
writing RSA key
```

and place these 4 files inside `keys` directory in root of the project
For more info on openssl, click [here](https://www.openssl.org/)

3. Setup environment variables
   Rename the `.env.example` as `.env` and fill up your details there.

**SendGrid**
Create an account at SendGrid [SendGrid](https://sendgrid.com/).
Create a new API Key [here](https://app.sendgrid.com/settings/api_keys)
Verify a sender email and use that email in the `.env` file, to verify click [here](https://app.sendgrid.com/settings/sender_auth/senders/new)

4. Place your application's Database credentials and config inside the `.env`.

Refer below config as example:

```js
const dev = {
  name: "dev",
  app: {
    port: process.env.PORT || 9000,
  },
  db: {
    name: `${process.env.DB_NAME}-dev`,
    host: process.env.DB_HOST,
    port: process.env.DB_PORT,
    username: process.env.DB_USERNAME,
    password: process.env.DB_PASSWORD,
  },
};
```

5. Install [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) and [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) in VS Code

6. Google and Facebook client details, [check out this article for generating client details](https://medium.com/@fayaz07/social-authentication-facebook-and-google-in-flutter-without-firebase-e3ca289ed50c)

7. Run the project with nodemon

```bash
npm run dev
```

or Run as normal project

```bash
npm start
```

7. Run tests

```bash
npm test
```
<!--
(#setup-gh-actions)
-->
## Setup GitHub actions

Mock environment values

```bash
# allowed-values: prod, dev, test
NODE_ENV=dev
PORT=5000

# mongodb
# Ex: remote mongodb host: my-app.xxxxx.mongodb.net
DB_NAME=node_template
DB_HOST=localhost
DB_PORT=27017
DB_USERNAME=
DB_PASSWORD=

# tokens
TOKEN_ISSUER=Node.js
TOKEN_AUDIENCE=API_USERS
TOKEN_SUBJECT=API_ACCESS
# Ex: For 1 day- 1d, for 1 second - 1s
REFRESH_TOKEN_EXPIRES=
ACCESS_TOKEN_EXPIRES=

# host
# for remote host=https://myapp.com
host=localhost:5000

# SENDGRID_API_KEY go here
SENDGRID_API_KEY=<API-KEY>
SENDGRID_EMAIL=john@doe.com
SENDGRID_USERNAME=John

# facebook client details
client_id=
client_secret=
```
Create such config locally in a text file or just copy the config from `.env` of your db, then head over to `Secrets` section of your repo, an ideal link would be like this https://github.com/username/node-rest-api-starter/settings/secrets when you replace `username` with your own github username, then create a new Secret there with key as `ENV_VARS_LOCALHOST` and the value as whole of your file which you have just created in the above step. When you make a pull request to the master branch this will get executed.

<!--
(#authors)
-->
## Authors

| ![image](https://avatars3.githubusercontent.com/u/35001172?s=128&v=4)                                                                                                                                                                                                                                                                                                                                                                         | ![image](https://avatars1.githubusercontent.com/u/20471162?s=128&v=4)                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [![LinkedIn](http://icons.iconarchive.com/icons/martz90/circle/32/linkedin-icon.png)](https://linkedin.com/in/fayaz07/) [![GitHub](https://icons.iconarchive.com/icons/artcore-illustrations/artcore-4/32/github-icon.png)](https://github.com/fayaz07/) [![Twitter](http://icons.iconarchive.com/icons/ampeross/smooth/32/Twitter-icon.png)](https://twitter.com/fayaz7_) [![Medium](public/images/medium.png)](https://medium.com/@fayaz07) | [![LinkedIn](http://icons.iconarchive.com/icons/martz90/circle/32/linkedin-icon.png)](https://linkedin.com/in/prudhvir3ddy/) [![GitHub](https://icons.iconarchive.com/icons/artcore-illustrations/artcore-4/32/github-icon.png)](https://github.com/prudhvir3ddy/) [![Twitter](http://icons.iconarchive.com/icons/ampeross/smooth/32/Twitter-icon.png)](https://twitter.com/https://twitter.com/prudhvir3ddy) [![Medium](public/images/medium.png)](https://medium.com/@prudhvir3ddy) |

<!--
(#contributing)
-->
## Contributing

Check [Contributing](CONTRIBUTING.md) file
