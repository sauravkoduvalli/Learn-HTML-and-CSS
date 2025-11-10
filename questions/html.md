# HTML Interview Questions and Answers

| No. | Question                                                                                                                                       |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is HTML?](#1-what-is-HTML)                                                                                                               |
| 2   | [Describe the basic structure of an HTML page?](#2-describe-the-basic-structure-of-an-html-page)                                               |
| 3   | [Why place `<script>` at the end of `<body>`?](#3-why-place-script-at-the-end-of-body)                                                         |
| 4   | [Explain difference between Elements and Tags in HTML?](#4-explain-difference-between-elements-and-tags-in-html)                               |
| 5   | [What are void elements in HTML?](#5-what-are-void-elements-in-html)                                                                           |
| 6   | [What is an attribute in HTML and it's different types?](#6-what-is-an-attribute-in-html-and-its-different-types)                              |
| 7   | [Explain the defer and async attributes used in `<script>` tag?](#7-explain-the-defer-and-async-attributes-used-in-script-tag)                 |
| 8   | [What is the difference between the `id` and `class` attributes?](#8-what-is-the-difference-between-the-id-and-class-attributes)               |
| 9   | [What is the purpose of the `alt` attribute in the `<img>` tag?](#9-what-is-the-purpose-of-the-alt-attribute-in-the-img-tag)                   |
| 10  | [What are the different ways to use CSS in HTML?](#10-what-are-the-different-ways-to-use-css-in-html)                                          |
| 11  | [How do you create `hyperlinks`? What are `absolute` vs `relative` URLs?](#11-how-do-you-create-hyperlinks-what-are-absolute-vs-relative-urls) |
| 12  | [What is the difference between an `anchor` tag and a `link` tag?](#12-what-is-the-difference-between-an-anchor-tag-and-a-link-tag)            |
|     | []()                                                                                                                                           |

---

## 1. What is HTML?

HTML (_HyperText Markup Language_) is the standard language used to create and structure content on the web. It consists of a series of elements that instruct the browser on how to display content such as text, images, links, tables, and forms. In simple terms, HTML acts as the skeletal structure of a webpage, defining its content and meaning. **HTML5** is the latest launched version in _2014_.

[⬆️Go to top](#html-interview-questions-and-answers)

## 2. Describe the basic structure of an HTML page?

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

[⬆️Go to top](#html-interview-questions-and-answers)

## 3. Why place `<script>` at the end of `<body>`?

Placing the `<script>` at the end of the `<body>` is to avoid the render bolcking. This will faster the content rendering and provide better user experience.

By default, when the browser encounters the `<script>` tag, it stops parsing the HTML until the script is downloaded and executed. If the script are in the `<head>`, the page may appear blank. Keeping the `<script>` at the end, allows browser to load and render the visible content first. The user sees the page quickly, even if the script takes time to load. Thus, users can start reading and interact with the content before JavaScript full loads.

[⬆️Go to top](#html-interview-questions-and-answers)

## 4. Explain difference between Elements and Tags in HTML?

In HTML, Tags are keywords consolsed within angle brackets that mark the beginning and end of an HTML element. They instruct the browser on how to interpret and display content. Most tags comes in pairs: an opening tag (e.g., `<p>`) and a closing tag (e.g., `</p>`).

Examples: `<p>`, `<h1>`, `<a>`, `<img>`, `<div>`.

An HTML element is a complete component of an HTML document, consisting of an opening tag, its content (if any), and a closing tag (if required). They define the structure and content of a webpage, such as paragraphs, headings, links, images, and more.

```html
<opening_tag>Content goes here</closing_tag>
```

[⬆️Go to top](#html-interview-questions-and-answers)

## 5. What are void or empty elements in HTML?

In HTML, some elements do not contain content and therefore they do not require a closing tag (e.g., `<br>`, `<img>`, `<input>`). These type of elements known as **void or empty elements** (_a.k.a self-closing elements_).

[⬆️Go to top](#html-interview-questions-and-answers)

## 6. What is an attribute in HTML and it's different types?

In HTML, an attribute provides additional information about an HTML element. Attributes are used to modify the behavior, appearance, or functionality of an element. They are always specified within the opening tag of an element.

```html
<element_name attribute_name="value">Content</element_name>
```

Most attributes consist of a _name_ and a _value_, separated by an _equals sign (=)_. The value is enclosed in quotation marks (_single_ or _double_).The different types of attribute are:

1. **Global Attributes**: can be used on almost all elements (e.g, `id`, `class`, `style`, `title`, `lang`).
2. **Element-Specific Attributes**: work only on particular elements (e.g., `<img>` -> `src`, `alt`, `width`, `height` and `<a>` -> `href`, `target`),
3. **Boolean Attributes**: true by presence, false by absence (e.g., `disabled`, `checked`, `readonly`, `multiple`, `required`, `defer`).
4. **Event Attributes**: attach JavaScript events directly (e.g., `onclick`, `onmouseover`, `onchange`, `onkeydown`)

[⬆️Go to top](#html-interview-questions-and-answers)

## 7. Explain the defer and async attributes used in `<script>` tag?

Both `defer` and `async` attributes in the `<script>` tag control how and when external JavaScript files are loaded and executed by the browser, thereby impacting page rendering performance.

**`defer` attribute**:

- The script is downloaded in parallel with HTML parsing, without blocking rendering.
- Execution happens after the HTML is fully parsed but before the `DOMContentLoaded` event.
- Best for scripts that depend on the DOM being completely built.
- Multiple `defer` scripts execute in the order they appear in the document.

**`async` attribute**:

- The script is downloaded in parallel with HTML parsing, also without blocking rendering.
- Execution happens immediately once the script is downloaded, even if HTML parsing isn’t finished.
- Best for scripts that are independent of the DOM (e.g., analytics, ads, tracking).
- The execution order is not guaranteed; whichever script finishes downloading first runs first.

| Attribute | Execution Timing               | Execution Order | DOM Dependency                                    |
| --------- | ------------------------------ | --------------- | ------------------------------------------------- |
| `async`   | Executes as soon as downloaded | Not guaranteed  | Suitable for scripts with no DOM dependency       |
| `defer`   | Executes after HTML parsing    | Preserved       | Suitable for scripts that require DOM to be ready |

[⬆️Go to top](#html-interview-questions-and-answers)

## 8. What is the difference between the `id` and `class` attributes?

An `id` attribute specifies a unique identifier for an HTML element within the entire document. An id should be used only once per page. It's often used for targeting specific elements with `JavaScript` or for creating internal links.

A class attribute specifies one or more class names for an HTML element. Multiple elements can share the same class, allowing you to apply the same styles or behaviors to a group of elements using `CSS` or `JavaScript`.

[⬆️Go to top](#html-interview-questions-and-answers)

## 9. What is the purpose of the `alt` attribute in the `<img>` tag?

The `alt` (alternative text) attribute provides a textual description of an image as a fallback display text, if the image fails to load. Its purpose is to:

- **Accessibility**: Provide context for visually impaired users who use screen readers.
- **SEO**: Help search engines understand the image content.

[⬆️Go to top](#html-interview-questions-and-answers)

## 10. What are the different ways to use CSS in HTML?

There are three primary methods to incorporate CSS into an HTML document.

1. External CSS:

   This method involves linking a separate `.css` file to your HTML document. This is generally the preferred approach for larger projects as it promotes code reusability and easier maintenance.

   ```html
   <head>
     <link rel="stylesheet" href="styles.css" />
   </head>
   ```

2. Internal CSS:

   Defined within the HTML document itself, specifically within a `<style>` element placed inside the `<head>` section. This is suitable for single-page applications or when specific styles are only relevant to a particular HTML file.

   ```html
   <head>
     <style>
       body {
         font-family: Arial, sans-serif;
       }
       h1 {
         color: blue;
       }
     </style>
   </head>
   ```

3. Inline CSS:

   Inline styles are applied directly to individual HTML elements using the `style` attribute. This method is typically used for minor, element-specific styling adjustments and is generally discouraged for extensive styling due to its lack of reusability and potential for messy code.

   ```html
   <p style="color: green; font-size: 16px;">This text is styled inline.</p>
   ```

[⬆️Go to top](#html-interview-questions-and-answers)

## 11. How do you create `hyperlinks`? What are `absolute` vs `relative` URLs?

A `hyperlink` is created using the `<a>` (anchor) tag and the `href` attributes says where the link goes. The content inside the tag is what people click on to visit another page or resource.

```html
<a href="https://www.example.com">Visit Example</a>
```

| Type         | Description                                                 | Behavior                                        | Example                                           |
| ------------ | ----------------------------------------------------------- | ----------------------------------------------- | ------------------------------------------------- |
| Absolute URL | Full web address with protocol and domain.                  | Always goes to the specified website.           | `<a href="https://www.example.com/page">Link</a>` |
| Relative URL | Path relative to the current page or site root (no domain). | Goes to a page within the same site or project. | `<a href="/page">Link</a>`                        |

[⬆️Go to top](#html-interview-questions-and-answers)

## 12. What is the difference between an `anchor` tag and a `link` tag?

The `<a>` (Anchor) tag and `<link>` tag serves distinct purposes in HTML, despite both being related to linking.

**`<a>` (Anchor) Tag**:

- It creates a hyperlink that users can click.
- It will be visible in the page (renders clickable text, image, or button-like elements).
- Used for navigation.

```html
<a href="#section2">Jump to Section 2</a>   <!-- Internal link -->
<a href="mailto:someone@example.com">Email me</a> <!-- Email link -->
```

**<link> Tag**:

- Defines a relationship between the current document and an external resource.
- This will not visible in the UI.
- Typically used in the `<head>` tag, commonly used for linking stylesheets, favicons, preloads, etc...

```html
<link rel="stylesheet" href="styles.css" />
<link rel="icon" href="favicon.ico" type="image/x-icon" />
<link rel="preconnect" href="https://fonts.googleapis.com" />
```

[⬆️Go to top](#html-interview-questions-and-answers)
