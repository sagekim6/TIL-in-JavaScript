# What is HTML?

- It is a markup language that tells web browsers how to structure the web page you visit.
- HTML consist of a series of elements.

### HTML Element

- Tags in HTML are not case-sensitive.`<p>`tag could be written as `<P>` and it will work.  
  however, it is best to write all tags in lowercase for sonsistency and readability.

```html
<p>My cat is grumpy</p>
```

![element](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-small.png)  
1.The opening tag  
2.The content  
3.The closing tag

-> The element is the opening tag, followed by content, followed by the closing tag.

#### Nesting elements

- Elements can be placed within other elements. This is called nesting.
- If you wanted to state that our cat is <strong>very</strong> grumpy, we could wrap the word 'very' in a `<strong>`tag.
- The tags have to open and close in a way that they are inside or outside one another.

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```

### Block VS Inline elements

#### Block-level elements

- Any content that follows a block-level element appears on a new line.
- Block-level elements are usually structural elements on the page. ex) headings, paragraphs, lists, or footer.
- Wouldn't nestes inside an inline element, but might be nested another block-level element.

#### Inline-level elements

- It will not cause a new line to appear in the document.
- Inline elements are contained within block-level elements.

```html
<em>one</em><em>two</em><em>three</em>
<p>four</p>
<p>five</p>
<p>six</p>
```

`<em>` is an inline element. the first three elements sit on the same line, with no space in between.  
On the other hand, `<p>` is a block-level element. Each `<p>` element appears on a new line.

#### Empty elements

- Not all elements has the pattern of an opening tag, content, and a closing tag.
- Some elements consist of a single tag, which is typically used to insert/imbed somthing in the document.  
  for example, the `<img>` element doesn't need a closing tag. It only embeds an image file onto a page.
- Empty elements are sometimes called void elements.

```html
<img scr="inlineBlock-level.PNG" />
```

### Attributes

Attributes contain extra information about the element that won't appear in the content.

An attribute should have:

- The attribute name, followed by an equal sign.
- An attribute value, wrapped with opening and closing quote marks.

```html
<a
  href="http://www.mozilla.org/"
  title="The Mozilla homepage"
  target="_blank"
></a>
```

- `href`: This attribute's value specify the web information ablut the link.
- `title`: The `title` attribute specifies extra information about the link. This appears as a tooltip when a cursor hovewrs over the element.
- `target`: The `target` attribute specifies the browsing context used to display the link. `target="_blank"` will display the link in a new tab.

#### Boolean attributes

Boolean attributes can only have one value, which is generally the same as the attibute name.

For example, the `disable` attribute can prevent the end user from entering text into the input box.

```html
<input type="text" disabled="disable" />
```

#### Omitting quates around attribute values

This is permitted in certain circumstances, but it can also break your markup in other circumstances.
For example from earlier, we used `href` attribute.

```html
<a href=http://www.mozilla.org></a>
```

- We can use without any quates when we will use only `href` attribute.

```html
<a href="http://www.mozilla.org/" target="_blank"></a>
```

- However, as soon as we add the `target` attribute in this way , it will cause error.  
  So always include the attribute quotes. It avoids such problems, and results in more readable code.

- single or double quotes...?  
  : You can feel free to choose which one you prefer. Both of these lines are equivalent.  
  Just make sure you don't mix single quotes and double quotes.  
  However, if you use one type of quote, you can include the other type of quote indise your attribute values.

```html
<a href="https://www.google.com" title="Let's goolge it!"></a>
```

### HTML document

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>test</title>
  </head>
  <body>
    <p>test page</p>
  </body>
</html>
```

1. `<!DOCTYPE html>`: The DOCTYPE declaration is an instruction to the web browser about what version of HTML the page is written in. However, nowadays the doctype is a historical artifact that needs to be included for everything.
2. `<html></html>`: This element wraps all the content on the page. It is sometimes known as the root element.
3. `<head></head>`: This element acts as a container for everythig you want to include on the HTML page,that isn't the content the page will show to viewers.
4. `<meta charset="utf-8" />`: This attribute tells the brower to use the utf-8 character encoding when translating machine code into human-readable text and vice versa to be displayed in the browser.
5. `<title></title>`: This set the title of the page, which is the title that appears in the browser tab the page is loaded in.
6. `<body></body>`: This contains all the content that displays on the page.

### Entity references: Including special characters in HTML

`<` `>` `"` `'` `&` These are parts of the HTML syntax itself. So if you want to use these characters you need to use this!
| Literal character | Character reference equivalent |  
|:------------------|:-------------------------------|  
|<| `&lt:` |  
|>|`&gt;` |  
|"|`&quot;`|  
|'|`&apos;`|  
|&|`&amp;`|
