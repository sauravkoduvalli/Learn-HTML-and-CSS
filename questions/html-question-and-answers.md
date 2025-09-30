# HTML Interview Questions and Answers

| No. | Question                                                                                       |
| --- | ---------------------------------------------------------------------------------------------- |
| 1   | [What is HTML?](#what-is-HTML)                                                                 |
| 2   | [Describe the basic structure of an HTML page?](#describe-the-basic-structure-of-an-html-page) |
| 3   | [Why place <script> at the end of <body>?](#why-place-script-at-the-end-of-body)               |
|     | []()                                                                                           |

---

## What is HTML?

HTML (_HyperText Markup Language_) is the standard language used to create and structure content on the web. It consists of a series of elements that instruct the browser on how to display content such as text, images, links, tables, and forms. In simple terms, HTML acts as the skeletal structure of a webpage, defining its content and meaning.

[⬆️Go to top](#html-interview-questions-and-answers)

## Describe the basic structure of an HTML page?

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Page Title</title>
  </head>
  <body>
    <!-- Page content goes here -->
  </body>
</html>
```

- **Document Type Declaration (`<!DOCTYPE html>`)**:

  This informs the browser which HTML version of the HTML is being used. It is not an HTML tag itself. In modern web development, `<!DOCTYPE html>` specifies HTML5.

- **HTML Root Element (`<html>..</html>`)**:

  The root element of every HTML document. This wraps all the other elements, signifies the start and end of a document. It often have the `lang` attribute to define the language of the document (e.g., `lang="en"`).

- **Head Section (`<head>..</head>`)**:

  This section contains metadata about the HTML document that is not directly displayed on the web page. Important elements within the `<head>` include:

  - **Title (`<title>`)**: Defines the title shown on the browser tab.
  - **Meta Tags (`<meta>`)**: Provide various types of metadata, such as character set (`charset="UTF-8"`), viewport settings for responsive design, and more.
  - **Link Tags (`<link>`)**: Used to link external resources, most commenly stylesheets (CSS).
  - **Style Tags (`<style>`)**: Allows enbedding internal CSS rules within the HTML document.
  - **Script Tags (`<script>`)**: Used to embed or link external javascript files.

- **Body Section (`<body>..</body>`)**:

  This section contains all the visible contents of the web page, including, texts, images, videos, links, forms, and other interactive elements.

## Why place <script> at the end of <body>?

Placing the `<script>` at the end of the `<body>` is to avoid the render bolcking, which will faster the content rendering and better user experience.

By default, when the browser encounters the `<script>` tag, it stops parsing the HTML until the script is downloaded and executed. If the script are in the `<head>`, the page may appear blank. Keeping the `<script>` at the end, allows browser to load and render the visible content first. The user sees the page quickly, even if the script takes time to load. Thus, users can start reading and interact with the content before JavaScript full loads.
