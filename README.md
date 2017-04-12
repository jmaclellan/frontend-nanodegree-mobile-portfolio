## Website Performance Optimization portfolio project

In part 1 of this project, I optimized index.html, showing Cameron's mock portfolio, so that it would achieve a
score over 90 on Google's PageSpeed Insights for both mobile and desktop. When I tested it, I was able
to achieve score of 94 for both mobile and desktop.

For part 2 of this project, I optimized pizza.html so that the page scrolls at 60 frames per second. Also, on that page
I optimized the resize pizza slider, so the the "Time to resize pizza" logs out to less than 5 milliseconds in the 
Chrome DevTools console.

## Development files (where work was done): index.html and main.js

## Production files: index-min.html and main-min.js

## Optimized pages on GitHub Pages:
### https://jmaclellan.github.io/frontend-nanodegree-mobile-portfolio/index-min.html
### https://jmaclellan.github.io/frontend-nanodegree-mobile-portfolio/views/pizza-min.html


####Steps taken to Optimize PageSpeed Insights score for index.html

* Used the website, Optimizilla.com, to compress the size of two jpeg images and add those newly optimized images 
(profilepic-min.jpg and pizzeria-min.jpg) to the project.

* Used Gimp, a free image editor availble online, in order to reduce the size of pizzeria-min.jpg, as the original
pizzeria.jpg had a natural size much larger than the display size which caused the page to be inefficient.

* Inlined CSS between style tags in the head

* Added media query (media="print") for print.css in order to block rendering

* Used async attribute on script tag for perfmatters.js in order to defer JavaScript rendering

* Used Google Web Font loader in head in order increase page speed as it doesn't have to load from a link

* Also minified index.html into index-min.html using the sites minifier.org for CSS and willpeavy.com for HTML


####Part 2: Optimize Frames per Second in pizza.html: Steps Taken

* Followed along with Cameron's answer for the Stop FSL quiz (I was a bit confused at first as the timeline in Chrome Dev Tools
had changed so much from the videos)

* Saved DOM nodes to the variable randomPizzas in order to avoid unnecessary repetition

* Removed the determineDx function and associated code as it was inefficient and unnecessary to resize pizzas

* Made the changePizzaSizes function so that it determines one of three widths, and then sets the width
for the pizza elements to match said widths

* Moved the variable items, which was in the updatePositions function, into the global scope so that it doesn't
need to be defined and queried each time you scroll

* In CSS, for the mover class, I added backface-visibility: hidden; in order to reduce a little bit of the FSL

* In the variable items, I changed document.querySelectorAll to document.getElementsByClassName as that
is much more efficient

* In the updatePosition function, the variable phase was calculating the same 5 unique repeating values, so I 
changed the code so that a for loop pushed those values into arrayX. Those values created the sine wave effect
of the pizzas. In line 507, the change to the background pizzas is made by multiplying phase and it now does so much more
effectively. 

* Also, in line 495, I took document.body.scrollTop and cached it as the variable topScroll for more efficieny

* Towards the end of the code, in the for loop in the event listener for when the page loads, I changed the number of pizzas 
from 200 to 32 as there was no need to generate pizzas that weren't visible on the screen
