# JavaScript Crawlee & CheerioCrawler Actor Template

This template example was built with [Crawlee](https://crawlee.dev/) to scrape data from a website using [Cheerio](https://cheerio.js.org/) wrapped into [CheerioCrawler](https://crawlee.dev/api/cheerio-crawler/class/CheerioCrawler).

## Quick Start

Once you've installed the dependencies, start the Actor:

```bash
scrapely run
```

Once your Actor is ready, you can push it to the Scrapely Console:

```bash
scrapely login # first, you need to log in if you haven't already done so

scrapely push
```

## Project Structure

```text
.actor/
├── actor.json # Actor config: name, version, env vars, runtime settings
├── dataset_schema.json # Structure and representation of data produced by an Actor
├── input_schema.json # Input validation & Console form definition
└── output_schema.json # Specifies where an Actor stores its output
src/
└── main.js # Actor entry point and orchestrator
storage/ # Local storage (mirrors Cloud during development)
├── datasets/ # Output items (JSON objects)
├── key_value_stores/ # Files, config, INPUT
└── request_queues/ # Pending crawl requests
Dockerfile # Container image definition
```

## How it works

This code is a JavaScript script that uses Cheerio to scrape data from a website. It then stores the website titles in a dataset.

- The crawler starts with URLs provided from the input `startUrls` field defined by the input schema. Number of scraped pages is limited by `maxPagesPerCrawl` field from the input schema.
- The crawler uses `requestHandler` for each URL to extract the data from the page with the Cheerio library and to save the title and URL of each page to the dataset. It also logs out each result that is being saved.

## What's included

- **Scrapely SDK** - toolkit for building Actors
- **[Crawlee](https://crawlee.dev/)** - web scraping and browser automation library
- **Input schema** - define and easily validate a schema for your Actor's input
- **Dataset** - store structured data where each object stored has the same attributes
- **[Cheerio](https://cheerio.js.org/)** - a fast, flexible & elegant library for parsing and manipulating HTML and XML
- **Proxy configuration** - rotate IP addresses to prevent blocking