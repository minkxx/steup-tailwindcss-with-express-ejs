# Setting Up Tailwind CSS v4.1 (CLI) with ExpressJS v5.1.0 and EJS (View Engine)

## Step 1: Initialize a New Node.js Project
Run the following command to initialize a new Node.js project:
```bash
npm init -y
```

## Step 2: Install Required Dependencies
Install the necessary dependencies using the commands below:
```bash
npm install tailwindcss @tailwindcss/cli
npm install express ejs
```

## Step 3: Create Required Files and Folders
1. Create a `public/css` directory and add a file named `input.css` inside it.
2. Create a `views` directory for `.ejs` files and add a file named `index.ejs` inside it.
3. Create a file named `index.js` in the root directory.

Ensure that your files are structured exactly as described.

## Step 4: File Contents
1. `public/css/input.css`:
    ```css
    @import "tailwindcss";
    ```

2. `views/index.ejs`:
    ```html
    <!doctype html>
    <html>
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <link href="/css/output.css" rel="stylesheet">
    </head>
    <body>
        <h1 class="text-3xl font-bold underline">
            Hello world!
        </h1>
    </body>
    </html>
    ```

3. `index.js`:
    ```javascript
    const express = require('express');
    const app = express();
    const port = 3000;

    app.set("view engine", "ejs");
    app.use(express.static('public'));

    app.get('/', (req, res) => {
        res.render("index");
    });

    app.listen(port, () => {
        console.log(`Application is running on http://localhost:${port}`);
    });
    ```

## Step 5: Update `package.json` Scripts
Add the following scripts to the `scripts` section of your `package.json` file:
```json
"scripts": {
    "watch:css": "npx @tailwindcss/cli -i ./public/css/input.css -o ./public/css/output.css --watch",
    "dev": "node index.js"
}
```

Refer to the `package.json` file for further clarification.

## Step 6: Run the Application
Use two separate terminal windows to execute the following commands:

1. To configure Tailwind CSS:
    ```bash
    npm run watch:css
    ```

2. To start the Express application:
    ```bash
    npm run dev
    ```

Your application should now be up and running.
