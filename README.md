# Example Website Documentation

This is the code for an example HTML/CSS website programmed by [Arthur Zarins](https://arthurzarins.com) to teach web development at [Dartmouth's Society of Computer Science Students](https://dsocss.github.io/website).

To view this website online, visit it's link at [(link not yet created)](https://arthurzarins.com).

This template is open for anyone to reuse, with the exception of the files in the `images` folder. Please use different photos on your own website unless you get permission otherwise.

Below in this README.md file are explanations of how the different HTML and CSS elements work together in this website.

# Table of Contents
1. [Links](#links)
1. [HTML](#html)
1. [CSS](#css)
1. [Additional Resources](#additional-resources)

## Links

It is practically impossible to create a website without having links. Links are needed for images, stylesheets, and allowing users to move between different websites (including different HTML pages); thus before writing any website code it's good to review the rules for relative and absolute links.

An absolute link, such as [https://dartmouth.edu](https://dartmouth.edu) directly points to the website. Absolute links are necessary for linking to webpages or other media that is not within your own website.

A relative link is frequently used to link files that are on the same website. Relative links have the advantage where they still work if you change your website's domain URL, and are a shorter length. For relative links, it is important to ensure that you are specifying the correct directory that the file is in. A relative link starts in the directory (folder) the link itself is contained in, and goes up however many specified directories.

- `.` means the current directory
- `..` means go up one directory
- `../..` means go up two directories
- `../../..` means go up three directories, and so on

After you have moved up the number of necessary directories, you can then move down into as many directories as needed until you enter the directory that has the file you want to retrive as a direct child of it.

As an example, let's say we have the following file/directory structure:

```
|
|--example
|   |--index.html
|
|--data
|   |--data2023.txt
|   |--data2024.txt
|
```

Given this directory structure, if we are in `index.html`, how can we create a link to retrive `data2024.txt` from `index.html`?

To retrive `data2024.txt`, we must do the following steps:
1. Go up one directory
2. Enter the `data` directory
3. Retrieve `data2024.txt`

The link to accomplish this would be `../data/data2024.txt`.

> [!NOTE]
> If your relative link starts with a slash `/` with no period before it then the relative link doesn't begin at the link's directory but instead the root directory. All other directory navigation rules still apply as normal.

## HTML

HTML, the acronym for HyperText Markup Language,

#### HTML Reference Sections
1. [HTML Head](#html-head)
1. [HTML Tags](#html-tags)
1. [HTML class](#html-class-attribute)

### HTML Head

At the top of the HTML document, we have an opening and closing `<head>` tag where we write general attributes of the webpage between them. Here is the head of our website:

```html
<head>
    <meta charset="utf-8">
    <title>Abby's Website</title>
    <link rel="icon" type="image/x-icon" href="./images/logos/icon.png">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="./css/style.css">
</head>
```

- `<meta charset="utf-8">` allows us to use the UTF-8 character set in the document, which contains characters in almost any alphabet you can think of
- In between the `<title>` tags, we can specify the website's title; in this case our title is "Abby's Website". The title shows up in the tab bar of the web browser and isn't on the page itself.
- `<link rel="icon" type="image/x-icon" href="./images/logos/icon.png">` lets us set a favicon image for the website in the `href` attribute; in this case our favicon image's link is `./images/logos/icon.png`. The favicon image is typically rendered at only 16x16 pixels and is rendered in the tab bar of the web browser, next to the document title.
- `<meta name="viewport" content="width=device-width, initial-scale=1">` tells the browser to use the device's actual width in calulations. Without this tag, we are unable to change the appearance of items depending on the browser's width, as on mobile phones the browser would pretend that we are on a wide desktop device.
- `<link rel="stylesheet" href="./css/style.css">` links our CSS stylesheet to the website, in this case the url to the stylesheet is `./css/style.css`. We are allowed to link multiple stylesheets to the document.

### HTML Tags

After the `<head>` in the HTML document, we have the rest of it in the `<body>`, with a corresponding closing tag of `</body>`.

Most HTML tags come in pairs, with an opening and closing tag. An opening tag looks like this: `<example>` and the corresponding closing tag looks like `</example>`.

- `<a href="">` Is a tag for a link. The `href` attribute is the URL the link points to, and anything between the opening and closing `<a>` tags are  
- `<p>` is a tag for a paragraph. Anything between the opening and closing `<p>` tags is inside the paragraph.
- `<h1>` is a tag for header 1, which is the largest header. `<h2>` is by default smaller than header 1, `<h3>` is smaller than that, and so on.
- `<img src="">` is a tag for an image; the src attribute specifies the link to the image file. Note that images are as large as their file's original size by default; the width/height are changed using CSS.
- `<div>` is a tag for a division or section in an HTML website that doesn't signify anything in particular.

### HTML class attribute

Any HTML element within the body can be modified to have a class attribute like the following:

```html
<p class="largeText">Some text in paragraph 1...</p>
<p class="largeText green">Some more text in paragraph 2...</p>
<p>The third paragraph...</p>
```

The first paragraph is a member of the `largeText` class. The second paragraph is a member of both the `largeText` and `green` class; when you want an element to belong to multiple classes list out the class names seperated by spaces. Finally, the third paragraph is a member of no class. You can create classnames of any kind, provided they don't contain any spaces. HTML class names are case sensitive.

Without CSS, the class attribute doesn't change how the HTML is rendered, but once we add CSS to the website we will then have the option to modify the display of *only* elements that are members of any specified class.

## CSS

CSS Stands for Cascading Style Sheets, which allow us to give instructions to the browser how we want our elements to be displayed.

#### CSS Reference Sections

1. [CSS calc()](#css-calc)
1. [CSS variables](#css-variables)
1. [CSS import](#css-import-statements)

### CSS calc()

CSS allows programmers to calculate values using the `calc()` function, which supports basic arithmetic such as `+ - * /`. Parenthesis can be used within the `calc()` function to override the default order of operations.

### CSS variables

CSS has support for variables. All variable names must start with two hyphen characters `--` and contain no spaces. To use a variable, you must use the `var()` wrapper function around the variable name like so: `var(--variableName)` where `--variableName` is replaced by the variable's name. It's common to store variable declarations in the `:root` selector at the top of the CSS file so the variable can be accessed anywhere else in the stylesheet.

### CSS import statements

CSS files can import other CSS files to be used as part of the stylesheet. To import another CSS file, write `@import url(../example/file/style.css)`, replacing `../example/file/style.css` with a link to your CSS file.

> [!IMPORTANT]
> CSS import statements must be at the top of the CSS file

## Additional Resources

Although you can write HTML and CSS files in almost any text-processing program, a coding editor such as [Visual Studio Code](https://code.visualstudio.com/) or [Sublime Text](https://www.sublimetext.com/) offers many more features and is easier to use, particularly with switching between files.

To learn more about web-development, a great resource is [Mozilla's MDN Web Docs](https://developer.mozilla.org/en-US/) which provides documentation on a wide range of CSS selectors and HTML tags. It also lists browser compatability for each CSS/HTML property on major browsers, so you can ensure that your program. 

> [!TIP]
> When testing your website, it's best to view it on different browsers and different devices (eg desktop, mobile) to ensure your site is displayed properly across platforms.

[GitHub Pages](https://pages.github.com/) allows you to publish your website for free, so long as you make the source code publicly available. Creating a GitHub account is free; for logging into GitHub from your computer, you might need [Git Credential Manager](https://github.com/git-ecosystem/git-credential-manager).