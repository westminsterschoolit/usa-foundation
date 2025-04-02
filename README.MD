# A Jekyll site for Westminster School's USA foundation

This repository is a very, very simple website for a Foundation event. It runs on Github pages after creation via an action. To develop use the instructions below. 

## Setting Up and Running the Jekyll Site

### Prerequisites
1. Install [Ruby](https://www.ruby-lang.org/en/documentation/installation/).
2. Install [Node.js](https://nodejs.org/) and npm (Node Package Manager).
3. Install [Bundler](https://bundler.io/):  
    ```bash
    gem install bundler
    ```
4. Install [Jekyll](https://jekyllrb.com/):  
    ```bash
    gem install jekyll
    ```

### Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/westminsterschoolit/usa-foundation.git
    cd usa-foundation
    ```

2. Install Ruby dependencies:
    ```bash
    bundle install
    ```

3. Install Node.js dependencies:
    ```bash
    npm install
    ```

### Running the Site
1. Build and serve the site locally:
    ```bash
    bundle exec jekyll serve
    ```

2. Open your browser and navigate to `http://localhost:4000`.

### Additional Commands
- To build the site without serving:
  ```bash
  bundle exec jekyll build
  ```
- To clean the `_site` directory:
  ```bash
  bundle exec jekyll clean
  ```

### Notes
- Ensure all dependencies are up to date by running:
  ```bash
  bundle update
  npm update
  ```
- For troubleshooting, refer to the [Jekyll documentation](https://jekyllrb.com/docs/).
