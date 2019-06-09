# Blue Prism tech test HTML/CSS version

You can view this HTML/CSS version of the tech test here : [https://eloquent-roentgen-3cd716.netlify.com/]

Thanks for asking me to submit this test. 

Rather than plunge straight into REACT I decided to work on the HTML & CSS of the solution standalone - this is my background and I still feel more comfortable working directly in the browser. My focus in this part of the build was to deal with the following: 

1. Ensure the site is responsive
2. Ensure the site is accessible
3. Make use of semantic HTML 5 elements
4. Construct a sensible SASS heirarchy implementing [BEM](https://getbem) 

It should be noted that I did not intend to make the HTML/CSS version render *_perfectly_* There are validation errors and I chose not to implement *all* the functionality here - it was really more about getting the responsive/semantic/accessible features down.

## Design
I decided not to make significant changes to the design as presented in the Sketch file - whilst there are undoubtedly some aspects of the design which may require thought, it is my belief that these issues are best addressed by testing the code with users rather than relying on my personal opinion. Where I *have* deviated form the design it is for accessibility reasons.

The only significant change I have made from the design is to implement the Progress bar as a HTML5 `progress` element which better matches its expected behaviour. I felt that the tiny text (especially when rendered over the blue/white background of the progress bar) would cause very significant accessibility issues for what might be quite important meta-information. I chose instead to present it in a straightforward list element which drops in under the `progress` bar. This approach also renders far more effectively on mobile.

## Framework
Given the comparatively short deadline I was given I decided to stick with a tried and tested, known framework rather than trying to either create a fully cross-browser compatible responsive render myself or try anything unproven. To that end I chose [spectre.css](https://picturepan2.github.io/spectre/) as a lightweight layout framework. This framework GZips down to just 10k and offers a minimal list of useful, tried and tested features alongside a bulletproof flexbox grid while not adding huge bloat to the site. As used here I have included the whole framework which in uncompressed, development mode adds 11.7k to the site. In a production environment the SASS version of the framework allows you to include only those elements required, allowing considerable additiponal savings to be made.

## Inline SVG Icons
In order to reduce the number of http requests, reduce overall file size, increase accessibility and improve the appearance across all channels I decided to implement Aria-tagged inline SVG for the icons (as described [here](https://www.24a11y.com/2018/accessible-svg-icons-with-inline-sprites/)) - The SVGs contain a `<title>` id which is referenced by a `aria-labelledby` tag ensuring the alt text is rendered both to the screen (on hover) and to assistive technology. This technique whilst offering a "belt and braces" approach to providing alternative text for the SVG *does come with a price*. 

([see here](https://css-tricks.com/youre-inlining-svg-icons-deal-unique-titles-ids/))

As you will see, this HTML version of the site fails W3C validation on IDs presented within the SVG images - an SVG is code, and paths within the SVG are often given IDs just like HTML elements - This issue has been obviated in the REACT version of the tech test by passing unique IDs to each instance of the SVG image.

## Style considerations (SASS/BEM)
I made the decision to stick with SASS to produce the styles for the tech test - Whilst I have had some exposure to JSS techniques I am not *entirely* convinced of their robust implementation out of design libraries - the onus is on the developer to produce (or interpret) the code - making the simple end-to-end transmission of clear guidelines from brand/design dependent upon the whim of the developer. I am cognisant however of the unique considerations required of component-based methodologies and so have adopted a BEM (block, element, modifier) based naming convention for all my styles.

## Responsive render
The site has been tested on desktop, mobile and tablet - it degrades gracefully to a 320px wide screen (iphone 5) while anything wider than 375px (iphone 6 +) renders perfectly. If I had longer I might choose to add a fixed header to the site for mobile - but I would nee dot see evidence of how many processes were likely to be displayed 