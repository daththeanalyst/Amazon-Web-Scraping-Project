## Overview

This project automates the process of monitoring the price of a specific T-shirt listed on Amazon. It uses web scraping to extract price and title information, stores this data, and checks for price changes. If the price drops below a certain threshold, the project sends an email notification to alert the user.

## Detailed Functionality

### Web Scraping

- The project connects to the Amazon product page using the `requests` library and fetches the HTML content of the page.
- It uses BeautifulSoup to parse the HTML and extract the product title and price.
- The product price is divided into its symbol, whole part, and fractional part to correctly format the price.

### Data Storage

- The product title, price, and the current date are saved to a CSV file named `AWSD.csv`.
- If the CSV file does not exist, it creates one and writes the headers (`Title`, `Price`, `Date`) along with the scraped data.
- If the CSV file already exists, it appends the new data without overwriting the existing entries.

### Price Monitoring

- The project defines a function `check_price()` that performs the scraping, data storage, and checks if the price has fallen below a specific threshold ($14 in this case).
- If the price is below $14, it triggers the `send_mail()` function to send an email alert.

### Email Notification

- The `send_mail()` function uses the `smtplib` library to connect to Gmail's SMTP server securely.
- It sends an email to a predefined address with a subject and body informing the user that the price has dropped below the set threshold.
- The email contains a link to the product page on Amazon where the user can purchase the T-shirt.

### Continuous Operation

- The `check_price()` function is called in an infinite loop with a delay of 24 hours (86400 seconds) between each check.
- This setup allows the script to run continuously in the background, checking the T-shirt's price daily.

## Summary

This project automates the monitoring of an Amazon product’s price, records the price data daily, and sends an email alert if the price drops below a specified threshold. It is useful for tracking price changes and ensuring that you don’t miss out on a good deal. The script is designed to run continuously, making it a hands-off solution for price monitoring.
