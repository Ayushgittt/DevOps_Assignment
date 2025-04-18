# DevOps_Assignment

•	How to build the Docker image:

    docker build \--build-arg SCRAPE_URL="https://webscraper.io/test-sites/e-commerce/allinone/computers/laptops" \-t 8192027760/web-scrapper_docker .

1.	Multi-stage build: I implemented a multi-stage Docker build using node:18-slim as the base image for the scraping stage and python:3.10-slim for the final stage.
2.	Build-time scraping: Scraping is performed during the image build process which is why the SCRAPE_URL is provided as a build-time argument. And also image size will be small. Also performing scraping at runtime would significantly increase the image size.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	How to run the container:

    docker run -p 5000:5000 -d 8192027760/web-scrapper_docker    

This allows the container to be accessed locally via http://localhost:5000

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	How to pass the URL to be scraped:

    docker build \--build-arg SCRAPE_URL="https://webscraper.io/test-sites/e-commerce/allinone/computers/laptops" \-t 8192027760/web-scrapper_docker .

By passing URL via SCRAPE_URL we can scrape any website

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
•	How to access the hosted scraped data:
Once the container is running, the scraped data is served via a Flask web server inside the container.
    http://localhost:5000
This URL returns the scraped data in JSON format. 
Run Container:-
    docker run -p 5000:5000 -d 8192027760/web-scrapper_docker
