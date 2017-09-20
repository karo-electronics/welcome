# H1
Text_H1

* [`name_ref0`](ref0#da-topic)  <- external file + heading
* [`name_ref0.2`](ref0)         <- external file **ONLY**
* [`name_ref1`][ref1]           <- internal


## H2
Text_H2

Text jumping to [Anchor - Headline - of the thing](#footnotes-appendix)

Text jumping to [Anchor - Inline - #anchor](#anchor)

Text jumping to [Anchor - Inline - hidden - #anchor_plus](#anchor_plus)

Text jumping to [Anchor - Inline - hidden #2 - #anchor_plus_plus](#anchor_plus_plus)

Now a separator & then some sweet lorem ipsum:

---

Sweet Lorem Ipsum:

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

---
## Footnotes & Appendix

[ref1]: https://example.com/test

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
https://example.com/test  
https://example.com/test  
[Nice text to an URI](https://stackoverflow.com/questions/5319754/cross-reference-named-anchor-in-markdown)  
https://github.com/gollum/gollum/issues/587

And, yes, they do work; but not without loosing the coherency of an URI, as it's
rendered as plain text. Only forcing a URI "resets" the FUBAR.

Hint: Never, **ever**, write anything close to a (bottom) separator, keep your
distance at all times, otherwise it looks like this:

This example text is no heading but as an example it shows what happens.
---

---
[Ka-Ro electronics GmbH](http://www.karo-electronics.de)  
Contact support: support@karo-electronics.de
