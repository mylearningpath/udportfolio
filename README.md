## Website Performance Optimization portfolio project

As part of Udacity's [Critical Rendering Path course](https://www.udacity.com/course/ud884) my challenge was to optimize this online portfolio for speed. In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques shown during the course.

---

## How to run the project

### Online Final Version

This is the link to the optimized version of the site: https://ronalson.github.io/udportfolio/


### Run Locally

1. Clone the repository

```bash
  $ git clone git@github.com:ronalson/udportfolio.git
```

2. Server the website:

Using Python

```bash
  $ python -m SimpleHTTPServer
```

or using [Atom Live Server Package](https://atom.io/packages/atom-live-server)

3. Open the website:

```bash
  $ open "http://localhost:8000"
```

---

## Project Specification - Website Optimization

### PageSpeed Score

- [x] _Critical Rendering Path_ - Get `index.html` achieves a PageSpeed score of at least **90 for Mobile and Desktop**.

##### Optimization Process

1. Reorganizing HTML @ index.html

  - add `media="print"` to `print.css` to reduce render blocking
  - `<script>` tags set to the bottom and add `async` attribute


2. Image Optimization

  - Apply corps and resizes to avoid unnecessary pixel rendering
  - Run images through optimization tool [TinyPNG](https://tinypng.com/)

### Getting Rid of Jank

- [x] _Frame Rate_ - Optimizations made to `views/js/main.js` make `views/pizza.html` render with a consistent **frame-rate at 60fps when scrolling**.

- [x] - _Computational Efficiency_ - Time to resize pizzas is less than 5 ms using the pizza size slider on the `views/pizza.html` page. Resize time is shown in the browser developer tools.

##### Optimization Process

1. Image Optimization

  - Apply corps and resizes to avoid unnecessary pixel rendering
  - Run images through optimization tool [TinyPNG](https://tinypng.com/)
  - Use responsive image techniques (i.e. `srcset`)


2. Fix `changePizzaSizes()` function

  - Remove repetitions
  - Remove unnecessary pixel creation from `determineDx` function
  - Remove DOM querying from inside the `for` loop


3. Fix `updatePositions()` function

  - Remove DOM geometry calculation from inside the `for` loop
  - Use CSS translate to move pizza instead of position.
  - Add `will-change: transform;` to `.move` class


4. Event Listener
  - call `updatePositions` with `requestAnimationFrame` on scrolling
  - call `updatePositions` with `requestAnimationFrame` on documentLoaded

5. Reduce number of pizza sliding 
