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
* [Git](https://git-scm.com/)
* 2 Ubuntu Linux Servers , Web and DB
* [Node.js](https://nodejs.org/) Version 14.15.3
* [PostgreSQL](https://www.postgresql.org/)
* [Free Okta developer account](https://developer.okta.com/) for account authentication.
* [PM2](https://pm2.keymetrics.io/)
* Basic linux knowledge

## Install and Configuration

1. Clone or download source files to both servers to a folder of choice using Git: `git clone https://github.com/BenTest12/bootcamp-app.git`
2. Install `Node.JS` Version 14.15.3 & `NPM` On both servers
3. Run `npm install` in the `bootcamp-app/` folder to install dependencies , run the command on both servers at the folder
4. If you don't already have PostgreSQL, install it on the DB Server by running `sudo apt-get install postgresql postgresql-contrib -y` at the DB Server
5. Create a [free Okta developer account](https://developer.okta.com/) and add a web application for this app 
   Under Applications -> Applications -> Create App Integration -> OIDC -> Web Application
6. Create the `.env` file in the `bootcamp-app/` project folder on both servers and change the `OKTA_*`, `Host Configuration` And `Postgress Configuration` values to your application

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

8. Initialize the PostgreSQL database by running `npm run initdb` from the `bootcamp-app/` project folder 
9. Run `npm run dev` in the Web Server , to start the `Weight Tracker` application 
10. Browse to `http://yourexternalserverip:8080` to view your `Weight Tracker` application

## Redundancy 

1. Install PM2 at the Web Server by running `sudo npm install pm2 -g` in the terminal
2. Run `pm2 startup` to initialize pm2 
3. Run `sudo env PATH=$PATH:/usr/local/bin /usr/local/lib/node_modules/pm2/bin/pm2 startup systemd -u ubuntu --hp /home/ubuntu` to configure pm2
4. Run `pm2 start src/index.js` from the project folder
5. Run `pm2 save` to save this configuration and enable redundancy in case of server reboot
