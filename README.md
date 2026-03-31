# Setup Apify CLI GitHub Action

## What is Apify?

[Apify](https://apify.com/) is a full-stack web scraping and automation platform where developers can build, deploy, and publish serverless microapps called Actors.

## What does Setup Apify CLI GitHub Action do?

This GitHub action sets up the Apify CLI in your GitHub Actions workflow. It installs the specified version of Apify CLI and logs you in with your Apify token, making it ready for use in subsequent workflow steps.

## Inputs

**version** (optional): Version of Apify CLI to install (e.g. "1.1.1", "latest", "beta"). Defaults to the latest stable version. Use "beta" to install the latest prerelease version.

**token** (required): Your Apify token for authentication. The CLI will be automatically logged in with this token. See the [Apify integration docs](https://docs.apify.com/platform/integrations/api#api-token) for instructions on how to find it.

## Example usage

### Basic setup with latest CLI version

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout sources
        uses: actions/checkout@v4

      - name: Setup Apify CLI
        uses: apify/setup-apify-cli-action@main
        with:
          token: ${{ secrets.APIFY_TOKEN }}

      - name: Use Apify CLI
        run: |
          apify --version
          apify create my-actor
```

### Setup with specific version

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout sources
        uses: actions/checkout@v4

      - name: Setup Apify CLI
        uses: apify/setup-apify-cli-action@main
        with:
          version: '1.1.1'
          token: ${{ secrets.APIFY_TOKEN }}
```

### Setup with latest beta (prerelease) version

```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout sources
        uses: actions/checkout@v4

      - name: Setup Apify CLI
        uses: apify/setup-apify-cli-action@main
        with:
          version: 'beta'
          token: ${{ secrets.APIFY_TOKEN }}
```

## Examples of top Actors on Apify Store

There are thousands of pre-built Actors on Apify Store. Check out some of the most popular:

- [Website Content Crawler](https://apify.com/apify/website-content-crawler): Crawl websites and extract text content to feed AI models, LLM applications, vector databases, or RAG pipelines.
- [Google Search Results Scraper](https://apify.com/apify/google-search-scraper): Extract organic and paid results, AI overviews, ads, queries, People Also Ask, prices, reviews, like a Google SERP API. 
- [Instagram Scraper](https://apify.com/apify/instagram-scraper): Scrape and download Instagram posts, profiles, places, hashtags, photos, and comments. 
- [Google Maps Email Extractor](https://apify.com/lukaskrivka/google-maps-with-contact-details): Scrape websites of Google Maps places for contact details and get email addresses, website, location, address, zipcode, phone number, social media links. 

## Additional resources

- Join 9,000+ web scraping and automation devs on the [Apify Discord](https://discord.com/invite/jyEM2PRvMU).
- [Apify documentation](https://docs.apify.com/): Platform guides and API references.
- [Apify open source](https://docs.apify.com/open-source): Apify's open-source libraries, including [Crawlee](https://crawlee.dev/), a web scraping and browser automation library for Node.js and Python.
- [Monetize your code](https://apify.com/partners/actor-developers): Share your Actors with the world and earn revenue whenever anyone uses them.
