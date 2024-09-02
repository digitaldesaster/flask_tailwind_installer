# Flask App with Tailwind CSS

This guide will help you set up a Flask application integrated with Tailwind CSS.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Project Setup](#project-setup)
3. [Virtual Environment](#virtual-environment)
4. [Install Flask](#install-flask)
5. [Install Tailwind CSS](#install-tailwind-css)
6. [Configure Tailwind CSS](#configure-tailwind-css)
7. [Create Your Flask Application](#create-your-flask-application)
8. [Create HTML Template](#create-html-template)
9. [Compile Tailwind CSS](#compile-tailwind-css)
10. [Run Your Flask Application](#run-your-flask-application)
11. [Package.json and Prettier Configuration](#packagejson-and-prettier-configuration)

## Prerequisites

- Ensure you have Python 3.10+, pip, and npm installed.

## Project Setup

1. **Create Project Directory**:
   ```bash
   mkdir flask_app
   cd flask_app
   ```

## Virtual Environment

1. **Create and Activate a Virtual Environment**:

   - **Create**:
     ```bash
     python3 -m venv .venv
     ```
   - **Activate**:
     - On **Windows**:
       ```bash
       .venv\Scripts\activate
       ```
     - On **macOS and Linux**:
       ```bash
       source .venv/bin/activate
       ```

## Install Flask

Install Flask within the virtual environment:

```bash
pip install flask
```

## Install Tailwind CSS

Install Tailwind CSS and its dependencies using npm:

```bash
npm install -D tailwindcss @tailwindcss/typography prettier prettier-plugin-tailwindcss
```

## Configure Tailwind CSS

1. **Initialize Tailwind CSS**:

   ```bash
   npx tailwindcss init
   ```

2. **Edit Tailwind Configuration**:
   Update the `tailwind.config.js` file:

   ```javascript
   /** @type {import('tailwindcss').Config} */
   module.exports = {
     content: ["./templates/**/*.html", "./static/js/**/*.js"],
     theme: {
       extend: {},
     },
     plugins: [],
   };
   ```

3. **Set Up Input CSS**:
   Create a CSS file for Tailwind (`static/src/input.css`):
   ```css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   ```

## Create Your Flask Application

Create a `main.py` file with the following content:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('main.html')

if __name__ == '__main__':
    app.run(debug=True)
```

## Create HTML Template

Create the main HTML file (`templates/main.html`):

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Flask App</title>
    <link
      rel="stylesheet"
      href="{{ url_for('static', filename='css/output.css') }}"
    />
  </head>
  <body class="flex items-center justify-center h-screen">
    <div class="container mx-auto">
      <h1 class="text-3xl font-bold text-center">Hello World</h1>
      <!-- Add your content here -->
    </div>
  </body>
</html>
```

## Compile Tailwind CSS

To compile your Tailwind CSS into a usable CSS file, you can set up scripts in your `package.json` or run a direct command:

In your `package.json`, you'll add scripts as follows:

```json
{
  "devDependencies": {
    "tailwindcss": "^3.4.10"
  },
  "scripts": {
    "build:css": "npx tailwindcss -i ./static/src/input.css -o ./static/css/output.css --minify",
    "watch:css": "npx tailwindcss -i ./static/src/input.css -o ./static/css/output.css --watch"
  }
}
```

Run the following command to compile:

```bash
npm run build:css
```

Or for continuous watching:

```bash
npm run watch:css
```

## Run Your Flask Application

Finally, start your Flask application:

```bash
python3 main.py
```

Your Flask app should now run at `http://127.0.0.1:5000/`, displaying the "Hello World" message styled with Tailwind CSS.

## Package.json and Prettier Configuration

To maintain a consistent code style, you can create a `.prettierrc.json` file in your project root with the following content:

```json
{
  "singleQuote": true,
  "semi": false,
  "trailingComma": "all"
}
```

This setup will ensure Prettier formats your code as per the specified rules when you save your files.
