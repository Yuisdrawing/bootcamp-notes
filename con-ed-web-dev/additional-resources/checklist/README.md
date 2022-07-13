# Debugging checklist
Is something not rendering the way you expected? 

Go through the list below to help you troubleshoot your work.

## HTML
* Are all of your tags closed?
* Are all the tags spelled correctly?
* Are `alt` attributes used on all images?
* Do images with important have detailed `alt` descriptions?
* Background images are used only where the design calls for a background image.
* Do the attributes have an opening and closing quotation? Are they the same type of quotation mark (single vs. double)?
* Is semantic HTML used correctly throughout your website?

## CSS
* Is the CSS linked correctly? Check your pathing to be sure.
* Are your classes spelled correctly?
* Are each of your CSS rules closed with a `}` bracket?
* Are there any styles being canceled out because of the CSS cascade?
* Do all properties end with a semi colon `;`?
* Do all media queries end with two `}` brackets.?
* Are two selectors targeting the same element and overriding each other due to specificity? 
* Are all background images being linked properly? Check the pathing to be sure.
* Do the colours in your CSS make sense of your colour scheme (i.e are all properties the colours they are meant to be instead of another colour specifying an error)?
* Are you working on an inline element but trying to give it a height?
