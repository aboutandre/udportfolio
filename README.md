# Website Performance Optimization portfolio project

## Getting started with the project

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [Grunt](http://gruntjs.com)
1. Navigate in Terminal to the project's root directory.
1. Install project dependencies with `npm install`.
1. Run Grunt with `grunt`.

### Optional
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights!
[More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)


## Optimizations

### PageSpeed Score
The following optimizations were performed to achieve a score of 94 (mobile) and 96 (desktop) for index.html:

1. JS and CSS are minified with Grunt
4. JS code was moved to the bottom of the page. Google Analytics, `perfmatters.js` and webfont are loaded async.
5. Critical CSS was inlined. `media="print"` was added to `print.css`

### Getting Rid of Jank

Optmizations to `main.js`

##### :424
  -  Changed the slider value to a percent width

##### :442
  -  Resizing of pizza containers

##### :463
  -  Took the var 'pizzasDiv' out of the loop since it's the same always

##### :497
  -  moved document.body.scrollTop to variable to keep it DRY
  -  this was brought outside the for loop because it's too costly inside

##### :502
  -  from querySelectorAll function by getElementsByClassName. As suggested [here](http://ryanmorr.com/abstract-away-the-performance-faults-of-queryselectorall/)

##### :527
  - Changed to requestAnimationFrame. As suggested [here](http://www.html5rocks.com/en/tutorials/speed/animations/)

##### :536
  - Reduced the pizzas from 200 to 30, 200 is overkill

##### :538
  - removed `width` and `height` attributes from JS

## References used in this project
- Udacity Forums
- [Webcasts for the Website Optimization Project](https://classroom.udacity.com/nanodegrees/nd001/parts/00113454012/modules/273584856175462/lessons/5988439100/concepts/68921686960923)
- [A smarter way to lear JS](http://www.asmarterwaytolearn.com/js/index-of-exercises.html)
- [JavaScript for Experienced Developers - Web Workers](https://youtu.be/LrK5HudphWY?list=PLbonu14zWhwygypsRytY17MRUk2sTK8kP)
- [Instant Loading with Service Workers (Chrome Dev Summit 2015)](https://youtu.be/jCKZDTtUA2A?list=PLbonu14zWhwygypsRytY17MRUk2sTK8kP)
- [Eloquent JavaScript](http://eloquentjavascript.net/)
