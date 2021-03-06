# web-price-scraper

## Overview
This project is meant to be a web scraper that runs server side and sends
alerts any time the price of a requested item has changed. It is planned to be
built to support:
* Amazon
* Allen Edmonds
* Uniqlo
* J. Crew
* The GAP

## Language
* Python3 w/ Beautiful Soup
* NodeJS w/ Express
* Angular 5

## Setup

```bash
cd service
pip3 install -r requirements.txt
cd ../client
npm install
cd web
ng build
cd ../../
```

Set environment variables for your MongoDB configuration:
```
MONGODB_USER
MONGODB_PASSWORD
MONGODB_DB
MONGODB_URI
```

These can also be stored in a `.env` file within `./client` and `./server`.

## Service - Execution

```bash
python3 service/main.py
```

## Client - Execution

```bash
node client/server.js
```

## Service - Installation

For now, I've just set up the service to run through my crontab once ever 12 hours.

```bash
# Web Price Scraper
0 8,20 * * * python3 ~/repos/web-price-scraper/service/main.py > /dev/null
```

## Client - Installation

Once you have downloaded this repository to your desired location, you can install the client
as a `systemd` service. Update `web-price-scraper.service` `WorkingDirectory` and `ExecStart`
parameters to point to the location of your cloned repository. Then execute the following:

```bash
cd client
sudo make install
```
