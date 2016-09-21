# extdesc
## Extended, Structured Descriptions in HTML
## Providing Extended Descriptions of Block and Inline Images, including Math

Proposal by Mark Hakkinen - Educational Testing Service - 21 September 2016

## Overview

This approach is being used at ETS, and was developed by the Accessibility, Standards, and Assistive Technology Research Group. Usability testing was conducted with screen reader users. Only existing HTML markup used.  There are no new features used.

## Block Images

The <figure> element is used to contain block images.  Within the <figure> element, is the visual image content, for example a graph or complex expression rendered using graphics.  The image has the aria-hidden attribute and it is set to true, meaning the image itself is hidden from screen readers.

The <caption> element is optional and should be used if the original image contains a visible caption.

A <div> element, functioning as the container for the extended description, follows. The <div> is visually hidden using standard CSS.

<figure>
		<div class="offscreen">
			<h1>Described image, Water Cycle</h1>
			<p>The diagram shows the processes of evaporation, condensation, evapotranspiration, water storage in ice and snow, and precipitation. The water table and ground water flow are also shown.</p>
		</div>
		<img src="watercycle.jpg" aria-hidden="true" alt="">
	</figure>

## Inline Images

An optional <span> element is used to contain inline images and their extended description.  Within the <span> element, is the visual image content, for example an image of a math expression rendered using graphics.  The image has the aria-hidden attribute and it is set to true, meaning the image itself is hidden from screen readers.

A <span> element, functioning as the container for the extended description, follows. The <span> is visually hidden using standard CSS.

<p>
		The approximate value of 
			<img alt="" src="sqrt3.png" aria-hidden="true">
			<span class="offscreen">the square root of three</span>
			<!-- <span class="offscreen">— nemeth follows: &gt;#3 </span> --> is 1.732. 
		Which of the following expressions gives the best approximation of 
			<img alt="" src="sqrt12.png" aria-hidden="true">
			<span class="offscreen">the square root of twelve</span>
			<!-- <span class="offscreen">— nemeth follows: &gt;#12 </span> --> ?
	</p>

