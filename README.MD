# A Jekyll site for Westminster School's USA foundation

This repository is a very, very simple website for a Foundation event. It runs on Github pages after creation via an action. To develop use the instructions below. 

It is currently configured for a single homepage, split into components via the _includes folder. The text content is controlled by markdown files. Once it gets more complex, more instructions will be added. 

## Simple text content

The small fragments of text are written in simple markdown files located in _includes/markdown 
For a quick introduction to Markdown syntax, refer to the [Markdown Guide](https://www.markdownguide.org/basic-syntax/). You can edit these easily if you have an account on Github and are added to this organisation. 

## Images

All images are located in the assets/images folder - very simple. These have been optimised. 

To optimize images for the website, you can use [Squoosh](https://squoosh.app/), a free and easy-to-use online tool. Squoosh allows you to compress images without significant loss of quality, reducing file sizes and improving page load times. Simply upload your image, adjust the compression settings, and download the optimized version to replace the original file.

## Donation form

The donation form is not yet configured to work as this needs to be sent via a third party as 
an embeddable piece of code. 

## Who asked for this site

Grace Green in March 2025. This has been built for low tech burden and uses Jekyll and Github actions to deploy to Github pages for free. 

## Domain name

This is configured in a CNAME file in the root of the site and will have multiple other domains redirected to it. The domain will point to: westminsterschoolfoundationus.org
The CNAME file should just contain a single line with the domain name, nothing else.

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

### Using PurgeCSS in the Production Build

To optimize the CSS for the production build and reduce bandwidth usage, this project uses [PurgeCSS](https://purgecss.com/). PurgeCSS removes unused CSS by analyzing the content of your HTML, JavaScript, and Markdown files, ensuring that only the styles actually used on the site are included in the final CSS file.

#### How It Works
1. **Scan Content Files**  
  PurgeCSS scans the project's HTML, JavaScript, and Markdown files to identify the CSS classes and styles in use.

2. **Remove Unused CSS**  
  Any CSS rules not referenced in the content files are removed from the final CSS file.

3. **Minify CSS**  
  The resulting CSS is minified to further reduce file size.

#### Integration in the Build Process
PurgeCSS is integrated into the production build process via the GitHub Actions workflow. During the build:
- The CSS files are processed by PurgeCSS to remove unused styles.
- The optimized CSS is included in the `_site` directory for deployment.

#### Benefits
- **Reduced File Size**: Smaller CSS files lead to faster page load times.
- **Improved Performance**: Less CSS means reduced bandwidth usage and better performance, especially for users on slower connections.
- **Cleaner Code**: Ensures that only necessary styles are deployed.

For more information on configuring PurgeCSS, refer to the [PurgeCSS documentation](https://purgecss.com/).

### Continuous Deployment with GitHub Actions

This repository is configured to use GitHub Actions for continuous deployment. There is no server architecture to maintain for the School. 

When changes are pushed to the `main` branch, a GitHub Action is triggered to rebuild the site and publish it to the `gh-pages` branch.

1. **Workflow File**  
  The deployment process is defined in the `.github/workflows/main.yml` file.

2. **Trigger**  
  The workflow is triggered automatically on every push to the `main` branch. You can also trigger this manually from the actions panel. 

3. **Build and Deploy**  
  The workflow:
  - Installs dependencies.
  - Builds the Jekyll site.
  - Purges unused CSS
  - Deploys the generated `_site` directory to the `gh-pages` branch.

4. **Live Site**  
  The `gh-pages` branch is configured to serve the site via GitHub Pages. Changes pushed to `main` will be live after the workflow completes.

For more details, refer to the workflow file in the `.github/workflows` directory.

### Configuring Vanilla-CookieConsent

To add a cookie consent banner using [Vanilla CookieConsent](https://github.com/orestbida/cookieconsent):

1. **Install Vanilla-CookieConsent**  
   Add the library to your project using npm:
   ```bash
   npm install vanilla-cookieconsent
   ```

2. **Import CSS via Sass**  
   Include the CookieConsent styles in your Sass file:
   ```scss
   @import 'node_modules/vanilla-cookieconsent/src/cookieconsent.scss';
   ```

3. **Initialize CookieConsent**  
   Add the following JavaScript code to initialize the cookie consent banner:
   ```javascript
   window.addEventListener('load', function () {
    const cc = initCookieConsent();

    cc.run({
     current_lang: 'en',
     autoclear_cookies: true,
     page_scripts: true,
     gui_options: {
       consent_modal: {
        layout: 'box',
        position: 'bottom',
        transition: 'slide'
       },
       settings_modal: {
        layout: 'box',
        transition: 'slide'
       }
     },
     languages: {
       en: {
        consent_modal: {
         title: 'We use cookies!',
         description: 'This website uses cookies to ensure you get the best experience on our website. <button type="button" data-cc="c-settings">Learn more</button>',
         primary_btn: {
           text: 'Accept all',
           role: 'accept_all'
         },
         secondary_btn: {
           text: 'Reject all',
           role: 'accept_necessary'
         }
        },
        settings_modal: {
         title: 'Cookie settings',
         save_settings_btn: 'Save settings',
         accept_all_btn: 'Accept all',
         reject_all_btn: 'Reject all',
         blocks: [
           {
            title: 'Necessary Cookies',
            description: 'These cookies are essential for the website to function properly.',
            toggle: {
             value: 'necessary',
             enabled: true,
             readonly: true
            }
           },
           {
            title: 'Analytics Cookies',
            description: 'These cookies help us understand how visitors interact with our website.',
            toggle: {
             value: 'analytics',
             enabled: false,
             readonly: false
            }
           }
         ]
        }
       }
     }
    });
   });
   ```

4. **Customize as Needed**  
   Modify the configuration to match your website's requirements, such as language, cookie categories, and banner styles.

5. **Test the Implementation**  
   Open your site locally and verify that the cookie consent banner appears and functions as expected.

For more details, refer to the [Vanilla CookieConsent documentation](https://github.com/orestbida/cookieconsent#readme).

## To do list

- [ ] Embed JavaScript form for donations.
- [ ] Add and finalize contact details section.
- [ ] Finalize the footer design and content.
- [ ] Repoint the domain name to the new site.