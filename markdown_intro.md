---
title: "R Markdown Tutorial"
author: "Cassandra"
date: "June 6, 2019"
output: 
  html_document: 
    keep_md: yes
---

Tutorial from https://www.markdowntutorial.com/.  
Side note: For text to be on a separate line when rendered in Markdown, you must have a double space at the end of the preceding line or else skip a line in your R markdown file. To get a proper header, you must skip a line before the header.

## R Markdown Basics

`_` or `*` = _italics_  
`**` = **bold**  
These can also be combined to make text both **_bold and italic_**.  

## Headers

There are six possible headers in decreasing size. Use a corresponding number of `#` to change header size. For example, `# Header 1` or `### Header 3`.

#### Headers can't be bold, but can be _italicized_

## Links

### Inline links

An inline link will directly link out to a website. To create an inline link in Markdown, include the visible text you want in brackets (`[]`) followed by the actual link in parentheses (`()`).   
Example: `[Use GitHub](www.github.com)`

Link text can be formatted like regular text.  
Example: `[**GitHub** is a great resource.](www.github.com)`

Links can even be included in headers.  

#### Getting started with [Github](www.github.com)

### Reference links

A reference link will reference a tag in the same document which then links out to a website. Reference links are useful if you're referencing the same place many times throughout your document because you only have to make one change to update everything that refers to that website.   
To create a reference link in Markdown, include the visible text in brackets (`[]`) followed by a tag in brackets (`[]`), which refers to a website at the end of the document.  

```
Here's [a link][tag] for you.
Here's [another link][another tag] for you.

[tag]: www.github.com
[another tag]: www.google.com
```
## Images

Images are similar to links, but marked with `!`. 

### Inline image link

Inline image links are just like inline links except they have `!` before the link.   

Example: `![A pretty tiger](https://upload.wikimedia.org/wikipedia/commons/5/56/Tiger.50.jpg)`

![A pretty tiger](https://upload.wikimedia.org/wikipedia/commons/5/56/Tiger.50.jpg)

### Reference image link

Similarly, reference images are the same as reference links except they have `!` before the link.

```
![A pretty tiger][Tiger]

[Tiger]: https://upload.wikimedia.org/wikipedia/commons/5/56/Tiger.50.jpg
```
## Blockquotes 

The blockquote format sets the text apart from the rest of the document by starting the line with `>`.  
Example: `> "Be yourself; everyone else is already taken."`  

You can make multiple lines part of one blockquote by including `>` on every line, even blank lines. 

> "Be yourself; everyone else is already taken." 
>
> --Oscar Wilde

Blockquotes can even include other formatting elements (like bold, italics, images, or links). 

## Lists

Creating an unordered list: 

* Start each item line with `*`   
* Put each item on its own line 
* Make sure that there is a blank line before the list starts  

Creating an ordered list: 

1. Start each item line with a number and `.` (like `1.`)  
2. Put each item on its own line  
3. Make sure that there is a blank line before the list starts  

Additional formatting elements can be used in lists, like bold, italics, or links. 

Lists can also be nested by adding a space at the beginning of each sub-list line so that it is one space over from the parent list lines.   
```
* Haddock
 * A sea captain
 * Has a fantastic beard
 * Loves whiskey
  * Possibly also scotch?
```
Lists can even incorporate multiple lines into one bullet point by indenting the extra lines. Blockquotes can also be included in lists this way. 

When making a list:

1. Decide what kind of list you want   
   Unordered or ordered?  
   
2. Decide how to format your list   
  *  **Bold**, _italics_, links, etc? 
  * Sub-lists?  
    * Requires `tab` in R markdown instead of `space`
  * Notes/paragraphs between bullet points?
 
## Paragraphs

### Soft breaks

To get a soft break, add two spaces at the end of a line. Then start the next line on the very next line in the markdown file.    
```
Soft breaks render with the lines together.  
Hard breaks render with the lines separated.
```
Soft breaks render with the lines together.  
Hard breaks render with the lines separated.

### Hard breaks 

To get a hard break, just skip a line between the lines of text. 
```
Soft breaks render with the lines together. 

Hard breaks render with the lines separated.
```
Soft breaks render with the lines together. 

Hard breaks render with the lines separated.

### Breaks in lists

Soft or hard breaks can be used in lists, depending on personal preference. 

Making a list:  

  * Soft breaks   
    Do you want to include soft breaks for notes?
  * Hard breaks   
  
    Or do you want to include hard breaks for notes?
