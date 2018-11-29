# H1
Text_H1

* [`name_ref0`](ref0.md#da-topic)  <- external file + heading
* [`name_ref0.2`](ref0)         <- external file **ONLY**
* [`name_ref1`][ref1]           <- internal

# Somekind of TOC

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [H1](#h1)
- [Somekind of TOC](#somekind-of-toc)
	- [H2](#h2)
		- [H3](#h3)
	- [Footnotes, Appendix & Sources](#footnotes-appendix-sources)
		- [Refs](#refs)
		- [Anchors](#anchors)
			- [Notes concerning: Anchors & self-closing tags](#notes-concerning-anchors-self-closing-tags)
			- [Notes concerning: Text placement](#notes-concerning-text-placement)

<!-- /TOC -->

## H2
Text_H2

Text jumping to [Anchor - Headline - of the thing](#footnotes-appendix)

Text jumping to [Anchor - Inline - #anchor](#anchor)

Text jumping to [Anchor - Inline - hidden - #anchor_plus](#anchor_plus)

Text jumping to [Anchor - Inline - hidden #2 - #anchor_plus_plus](#anchor_plus_plus)

Text jumping to [Anchor - Inline - hidden #3 - #anchor_plus_plus_many](#anchor_plus_plus_many)

Text jumping to [Anchor - Inline - hidden #4 - #anchor_plus_plus_many2](#anchor_plus_plus_many2)


Let's jump to [The H3 Chapter](#h3)

Now a separator & then some sweet lorem ipsum:

---

Sweet Lorem Ipsum

Adipisci nisi molestiae blanditiis. Dolorum sit autem non quis et ut non.
Placeat dolores rerum in necessitatibus. Voluptatum accusantium officia eius
quod incidunt iure. Illum fuga est eum molestias similique provident neque.

Iusto quam asperiores aut repellat. Laudantium quia quia ut repudiandae quas
adipisci autem. Quo recusandae in aliquam dolore eius.

Quisquam sequi aliquid quasi vero quibusdam id voluptatem velit. Ea quia qui
quas est atque eligendi ut. Atque adipisci iste consectetur exercitationem.

Velit veniam qui magnam ut soluta inventore fugiat qui. Accusamus voluptas sed
eaque. Fuga consectetur occaecati est pariatur repellat veniam. Ipsum omnis
dolorum et ut nihil omnis mollitia. Quia cupiditate ipsum nostrum voluptatem.
Qui ducimus amet et omnis error et.

Quidem minima explicabo laboriosam dolore mollitia. Saepe placeat similique
sapiente qui. Eveniet ipsum voluptatibus non corrupti enim minima nam. Sit sunt
nemo fuga iure ad asperiores.

Qui eum culpa aliquam voluptas laboriosam vel esse. Architecto nihil quia magnam
ullam corporis. Esse dolorum amet ullam vel. Ad aut fugit aperiam explicabo
autem ut quod et. Omnis soluta illum eum eveniet.

Ut illo sapiente est. Nostrum ut laudantium qui incidunt est molestias fugiat. A
fugiat sint natus. Omnis ut aut qui voluptatem molestiae perferendis. Numquam
cupiditate sed corrupti quaerat.

Sit alias necessitatibus vitae eveniet perferendis voluptas libero. Labore
excepturi quo mollitia rem perferendis ipsum repellendus minima. Quidem ipsa
sint aut numquam sit dolorem blanditiis.

Maxime laudantium distinctio cum accusamus in velit doloremque consequatur.
Dolor voluptatum eos iure. Reprehenderit perferendis laboriosam aliquid.
Blanditiis sapiente cum modi et deserunt aut excepturi.

Expedita et fugit expedita magni qui perspiciatis cumque. Aut et eaque
voluptatibus molestiae quae quis atque ut. Repudiandae dignissimos incidunt est
ut nemo. Quidem in molestias eius mollitia et ut in mollitia.

### H3
Text_H3

---
## Footnotes, Appendix & Sources

### Refs
(everything of interest herein actually requires a text editor to been seen)

[ref1]: https://example.com/test

### Anchors
<a id="anchor">#anchor with a name</a>  
Where you find more about this:  
https://github.com/gollum/gollum/issues/587  
https://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown  
https://stackoverflow.com/questions/27981247/github-markdown-same-page-link  
https://stackoverflow.com/questions/6695439/how-to-link-to-a-named-anchor-in-multimarkdown  

<a id="anchor_plus"></a>Hidden Anchor  
https://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown  

btw.:  
Probably also a `<a id="anchor_plus"/>` (self-closing [XML/HTML5] tag) works:

<a id="anchor_plus_plus"/>Hidden Anchor #2  
More Text after the actual anchor "name"  
https://example.com/test1  
https://example.com/test2  
[Nice text to an URI](https://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown)  
https://github.com/gollum/gollum/issues/587

And, yes, they do work; but not without loosing the coherency of an URI, as it's
rendered as plain text. Only forcing a URI "resets" the FUBAR.

#### Notes concerning: Anchors & self-closing tags
A self-closing anchor reference **will** "anchor" all the text behind it thus
making the construct look like the following:

<a id="anchor_plus_plus_many"/>Hidden Anchor #3  
this next line IS still an clickable URL with the same anchor.

_Source:_
```html
<a id="anchor_plus_plus_many"/>Hidden Anchor #3  
this next line IS still an clickable URL with the same anchor.
```

This will either go on either till (see "Hidden Anchor #4") a hard linebreak or
the next HTML tag (see above: "Hidden Anchor #2").

<a id="anchor_plus_plus_many2"/>Hidden Anchor #4  

this next line is NOT an clickable URL with the same anchor. Because hard line break.

_Source:_
```html
<a id="anchor_plus_plus_many2"/>Hidden Anchor #4  

this next line is NOT an clickable URL with the same anchor. Because hard line break.
```

To rectify this one **needs** to use a closed HTML tag (see above: "Hidden Anchor"):

_Source:_
```html
<a id="anchor_plus"></a>Hidden Anchor  
https://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown  
```

---

#### Notes concerning: Text placement
**Hint:**  
Never, **ever**, write anything close to a (bottom) separator, keep your
distance at all times, otherwise it looks like this:

This example text is no heading but an example, which shows what happens if you don't keep your distance to following element(s); in this case that of a (supposed) separator (`---`).
---

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de