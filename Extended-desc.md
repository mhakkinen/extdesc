# Providing Extended Descriptions of Block and Inline Images, including Math

Proposal by Mark Hakkinen - Educational Testing Service - 21 September 2016

## Overview

This approach was developed by the ETS Accessibility, Standards, and Assistive Technology Research Group.  The approach is specifically intended for content in assessments where the extended description is *not* displayed visually and is available to screen reader users.  Usability testing was conducted with screen reader users. Only existing HTML markup is used.  There are no new features used.

## Block Images

The `<figure>` element is used to contain block images.  Within the `<figure>` element, is the visual image content, for example a graph or complex expression rendered using graphics.  The image has the aria-hidden attribute and it is set to true, meaning the image itself is hidden from screen readers.

The `<caption>` element is optional and should be used if the original image contains a visible caption.

A `<div>` element, functioning as the container for the extended description, follows. The `<div>` is visually hidden using standard CSS.

``` HTML
<figure>
		<div class="offscreen">
			<h1>Described image, Water Cycle</h1>
			<p>The diagram shows the processes of evaporation, condensation, evapotranspiration, water storage in ice and snow, and precipitation. The water table and ground water flow are also shown.</p>
		</div>
		<img src="watercycle.jpg" aria-hidden="true" alt="">
	</figure>
``` 

### Note Regarding Visibility

In contexts where extended descriptions are visible, there are multiple approaches possible.  For example, it is possible to utilize a `<details>` element to contain and allow for exposing the description, with options to position or style the extended description to suit layout requirements, such as an overlay, above, below, or adjacent to the image.  Other programmatic or static options are possible.




## Inline Images

An  `<span>` element is used to contain inline images and their extended description.  Within the `<span>` element, is the visual image content, for example an image of a math expression rendered using graphics.  The image has the aria-hidden attribute and it is set to true, meaning the image itself is hidden from screen readers.

A `<span>` element, functioning as the container for the extended description, follows, contained in the parent '<span>'. The `<span>` is visually hidden using standard CSS.  Read Aloud tools would consume the spanned, structured description. No alt text is supplied for the image.  It would be expected that a Read Aloud tool can highlight the visible content of the parent span, e.g. by drawing a border, or visually applying a color highlight on the image.

``` HTML
<p>
		The approximate value of 
			<span id="describedInline1"><img alt="" src="sqrt3.png" aria-hidden="true">
			<span class="offscreen">the square root of three</span></span> is 1.732. 
		Which of the following expressions gives the best approximation of 
			<span id="describedInline2"><img alt="" src="sqrt12.png" aria-hidden="true">
			<span class="offscreen">the square root of twelve</span>
			<span class="nemeth">&nbsp;Nemeth follows: &gt;#12 </span>?
	</p>
```

In the example above, the second described inline image also includes a Nemeth braille description. While we don't suggest this as finalized, we do suggest this approach allows nesting of alternates, such as standard text descriptions, braille, or simplified text, that could be selected programmatically or via CSS as determined by a user profile or PNP.

##  Extensibility: Toward DIAGRAMMAR

This approach, in its simplicity also permits extensibility. Within the `<figure>` element approach for block images, one can supply multiple, sequential or nested alternate blocks, containing specific content such as simplified descriptions, descriptions and tours for related embossed content, etc. Further, hyperlinks or buttons (for example) could be provided instead of inline textual content.

### Description Semantics, Labelling, and Navigation

What is missing in this approach are semantics.  ARIA 1.1 features such as `aria-roledescription` or `aria-label` can provide a workable solution for human understandable labels that could facilitate region navigation by screen reader users, for example, within the `<figure>` contents, pending future availability of new ARIA role semantics suited to the task.

Finally, this approach can map to the semantically (and operationally) richer model ETS has proposed for using web components to directly support DIAGRAMMAR semantics and structure in HTML. [1]


## Robust Hiding/Exposure of Alternates

Programmatic or CSS based hiding of alternative content within children nested within the `<figure>` or inline `<span>` elements is achievable.  However, based on discussions at TPAC 2016, Media Queries may provide a robust, "automatic" model for content selection based on user media requirements.  We await further developments on the media query front.


# References

[1] https://github.com/mhakkinen/dg-content





