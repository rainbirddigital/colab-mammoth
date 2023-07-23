# Google Colab implementation of Mammoth .docx to HTML converter

[Mammoth](https://github.com/mwilliamson/python-mammoth) converts .docx documents into a semantic HTML. This [Google Colab](https://colab.research.google.com) implementation utilizes Mammoth and additionally adds a responsive header and footer to each of the exported HTMl files. This process requires some basic knowledge of Word or similar open-source alternatives such as [OnlyOffice](https://www.onlyoffice.com), HTML/CSS and a free [Google Drive](https://drive.google.com) account.

---

## Word .docx Preparation

The structure of .docx and HTML are quite different, so only particular Word paragraph and character styles can be converted by default. The demo file `mammoth-demo.docx` included in this repository utilizes some core Word styles and a number of custom styles for block quotes, captions and so forth. Refer to the full [Mammoth documentation](https://github.com/mwilliamson/python-mammoth) for details on how Mammoth can be further customised. 

### Core .docx styles
The following default Word styles are automatically converted into HTML equivalents: Headings 1 to 6, Paragraphs, Line breaks, Lists, Hyperlinks, Tables, Footnotes and Text styles including Bold, Italic, Underline, Strikethrough, Superscript, Subscript.  

### Blockquotes
Blockquotes require that a custom Word paragraph style `Quote` is applied to text. This is then converted into the following HTML `<blockquote class="quote">`Text Here`</blockquote>`

### Captions
Captions require that a custom Word paragraph style `imageCaption` is applied to text. This is then converted into the following HTML `<figcaption class="imageCaption">`Text Here`</figcaption>`

### Bibliography or References
Biblographic elements require a custom Word paragraph style `bibloReference` to be applied to appropriate footer text. This is converted into the following HTML `<p class="bibloReference">`Reference Text`</p>` and creates an indented effect in the final document. Note the reference links themselves can convert unreliably within Mammoth, so they may need to be checked and added manually. 

### Copyright Notice
The copyright notice requires that a custom Word paragraph style `copyrightMeta` is applied to appropriate text. Javascript within the HTML file automatically moves this text to the base of the HTML file. The converted HTML appears in the following format `<div class="copyrightMetaFooter"><p class="copyrightMeta">`Text Here`</p></div>`

### Tables
Mammoth supports basic tables and merged table cells in both horizontal and vertical axis. Table headings should use the standard Word heading styles. Table captions should use the above `imageCaption` style. 

---

## HTML Preparation and Output

This repository contains two files `header.htm` and `footer.htm` that can be adapted to alter the presentation of the output HTML files. The header file `header.htm` contains inline CSS that controls the layout, fonts, colors and text sizes of all elements, alongside some custom styles that can be applied manually to the exported files to improve the layouts. 

### Fonts
The output HTML uses free open-source [Google Fonts](https://fonts.google.com) 

### Tables
A wrapper tag is automatically added around tables, which facilitates horizontal scrolling on small devices `<div class="tableWrap"><table>`Table Content`</table></div>` 

The css additionally features other styles for table headers and striped rows. These must be added manually to the output HTML files: 
* To add a table header. Wrap the table row in the following HTML `<thead><tr>`Table header content here`</tr></thead>`
* To add a striped row effect. Wrap the table body in the following HTML `<tbody class="zebraTable"><tr>`Table body content here`</tr></tbody>`

### Images   
Images are directly embedded into the html document. It is possible within Mammoth to save them externally, refer to the full [documentation](https://github.com/mwilliamson/python-mammoth) for details.

### Footnotes   
Footnotes automatically appear at the base of the HTML file

### Ordered Lists
Ordered lists that require special numbering formats require the manual addition of the following CSS styles to a lists `<ol>` tag:
* `1. 2. 3. 4.` is the default behavior of `<ol>`List Here`</ol>`
* `i. ii. iii.` = `<ol class="listLowerRoman><li>`List Here`</li></ol>`
* `I. II. III.` = `<ol class="listUpperRoman><li>`List Here`</li></ol>`
* `a. b. c.` = `<ol class="listLowerLatin><li>`List Here`</li></ol>`
* `A. B. C.` = `<ol class="listUpperLatin><li>`List Here`</li></ol>`
* `No bullets` = `<ol class="listNone><li>`List Here`</li></ol>`

---

## Google Colab Conversion and Export
Open the link below or copy the file `Mammoth.word-docx-to-html-github.ipynb` from the repository to your Google Drive and open in [Google Colab](https://colab.research.google.com). Follow the notebook instructions to complete the conversion process.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Ma_-5nClXoDsH65vPX3eL0ERwcTezJFo?usp=sharing)
