
# YouTube Comment Search API

This Flask-based API allows you to search for comments from a YouTube video using various search criteria, such as author name, date range, like and reply counts, and text content.

## Prerequisites

Before running this application, ensure you have the following dependencies installed:

- Python (3.7 or higher)
- Flask (installed via `pip install Flask`)
- [Zappa](https://github.com/Miserlou/Zappa) (for deployment to AWS Lambda)

## Getting Started

1. Clone this repository to your local machine:

   ```bash
   git clone <repository-url>
   cd youtube-comment-api
   ```

2. Set up a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use: venv\Scripts\activate
   ```

3. Install project dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Run the Flask app locally:

   ```bash
   python app.py
   ```

   The app will be accessible at `http://localhost:5000`.

## API Endpoints

### Search Comments

You can search for comments using various criteria:

- `search_author`: Search by author name.
- `at_from` and `at_to`: Search by date range.
- `like_from` and `like_to`: Search by like count range.
- `reply_from` and `reply_to`: Search by reply count range.
- `search_text`: Search by text content.

#### Example API Calls

- To search for comments by author "Channel Makers":

  ```
  http://localhost:5000/search?search_author=Channel%20Makers
  ```

- To search for comments posted between January 16, 2023, and January 25, 2023:

  ```
  http://localhost:5000/search?at_from=2023-01-16&at_to=2023-01-25
  ```

- To search for comments with at least 10 likes and 5 replies:

  ```
  http://localhost:5000/search?like_from=10&reply_from=5
  ```

- To search for comments containing the word "monetized":

  ```
  http://localhost:5000/search?search_text=monetized
  ```

- You can also combine multiple search criteria in a single request.

## Deployment to AWS Lambda

To deploy this Flask app to AWS Lambda using Zappa, follow these steps:

1. Install Zappa:

   ```bash
   pip install zappa
   ```

2. Initialize Zappa:

   ```bash
   zappa init
   ```

   Follow the prompts to configure your deployment settings.

3. Deploy to AWS Lambda:

   ```bash
   zappa deploy dev  # 'dev' is the environment name; you can use any name you like
   ```

   Zappa will package your Flask app and create a Lambda function for it.

4. Get the API Gateway URL:

   After deployment, Zappa will provide you with an API Gateway URL. This URL is where your API will be accessible.

