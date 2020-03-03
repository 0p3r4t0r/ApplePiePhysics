# Apple Pie Physics

The name for this project is inspired by a quote from the 1980 television series Cosmos: A Personal Voyage.

"If you wish to make, an apple pie from scratch, you must first invent the universe."
-- Carl Sagan


## Knowledge Shrinks Time and Space
While most of the cosmos remains beyond the reach of our lifetimes, the miracle of our minds
provides us with the faculties to explore and imagine the otherwise unreachable cosmos.




## Tech Stack
*   [Hugo: Static Site Generator](https://gohugo.io/)
*   [Cupper Theme](https://themes.gohugo.io/cupper-hugo-theme/)
*   [Katex](https://katex.org/)
*   [Processing](https://processing.org/)/[Processing.js](http://processingjs.org/)
*   [Desmos Graphing API (Hopefully)](https://www.desmos.com/api/v1.4/docs/index.html)




## Conventions
Rules schmules, but organization matters.


### Filename Conventions
*   Directories in the content folder should have names corresponding to those
    specified in the nav with all spaces replaced with hyphens.

*   Lessons in the content folder should have names of the form 
    `lesson<number>_descriptionOfTheLesson.<filename extension>`.


### Processing Conventions
Because processing.js is not able to support external libraries, the programs for the
website must be written without any external libraries.

#### Setup: Coordinates and Framerate
*   Move the coordinates to the center of the screen.
    ```processing
    void centerCoors() {
      // Make (0, 0) the origin.
      translate(width/2, height/2);
      scale(1.0, -1.0);
    }
    ```
    Reference: [Processing Docs: 2D Transformations](https://processing.org/tutorials/transform2d/).

*   The framerate should be set to 50 fps. This framerate is low enough that virtually any
    computer can achieve it, and it makes calculations involving time much easier. If, you
    need to use a different framerate for any reason be sure to make a note of it in the 
    [units comment](#Real-World Units).
    ```processing
    void setup() {
      frameRate(50);
      // The rest of your setup.
    }
    ```
    Reference: [Processing Docs: frameRate](https://processing.org/reference/frameRate_.html).

#### Real-World Units
*   At the very top of each sketch, the scale for the units should be specified in a **units comment**.
    Just below the units comment save the fps and the amount of real time per frame.
    ```processing
    \* Units Comment
      1 meter = 20 px
      1 second = 50 frames
      ... etc.
    *\
    int fps = 50;           // frames per second
    float spf = 1.0 / fps;  // seconds per frame
    ```
