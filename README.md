# Node.js Weight Tracker

![Demo](docs/build-weight-tracker-app-demo.gif)

This sample application demonstrates the following technologies.

* [hapi](https://hapi.dev) - a wonderful Node.js application framework
* [PostgreSQL](https://www.postgresql.org/) - a popular relational database
* [Postgres](https://github.com/porsager/postgres) - a new PostgreSQL client for Node.js
* [Vue.js](https://vuejs.org/) - a popular front-end library
* [Bulma](https://bulma.io/) - a great CSS framework based on Flexbox
* [EJS](https://ejs.co/) - a great template library for server-side HTML templates

**Requirements:**

* 2 Servers , Web and DB
* [Node.js](https://nodejs.org/) 14.15.3
* [PostgreSQL](https://www.postgresql.org/) 
* [Free Okta developer account](https://developer.okta.com/) for account authentication.

## Install and Configuration

1. Clone or download source files to both servers
2. Install Node.JS Version 14.15.3 & NPM On both servers
3. Run `npm install` in the repository folder to install dependencies , on both servers 
4. If you don't already have PostgreSQL, install it on the DB Server
5. Create a [free Okta developer account](https://developer.okta.com/) and add a web application for this app 
6. Under Applications -> Applications -> Create App Integration -> OIDC -> Web Application
7. Create `.env` file and change the `OKTA_*` values to your application

```yml
  # Host configuration
  PORT=8080
  HOST=*HOST*
  NODE_ENV=development
  HOST_URL=http://*HOSTURL*:8080
  COOKIE_ENCRYPT_PWD=superAwesomePasswordStringThatIsAtLeast32CharactersLong!

  # Okta configuration
  OKTA_ORG_URL="https://*OKTA_DOMAIN_URL*.okta.com"
  OKTA_CLIENT_ID="*CLIENTIDPASSWORD*"
  OKTA_CLIENT_SECRET="*WEB_APP_INTEGRATION_SECRET*"

  # Postgres configuration
  PGHOST=*POSTGRESS_HOST*
  PGUSERNAME=*POSTGRESS USER*
  PGDATABASE=*POSTGRESS DB*
  PGPASSWORD=*POSTGRESS PASSWORD*
  PGPORT=5432
```

4. Initialize the PostgreSQL database by running `npm run initdb`
5. Run `npm run dev` in the Web Server , to start the Node.JS application

The associated blog post goes into more detail on how to set up PostgreSQL with Docker and how to configure your Okta account.




