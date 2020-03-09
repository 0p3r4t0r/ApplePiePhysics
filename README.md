# Apple Pie Physics

The name for this project is inspired by a quote from the 1980 television 
series Cosmos: A Personal Voyage.

> If you wish to make, an apple pie from scratch, you must first invent the 
> universe.
>
> Carl Sagan


## Knowledge Shrinks Time and Space
> When revisiting places we once frequented as children, it is not unusual to 
> observe how much smaller everything seems. This experience has too often been
> attributed to the physical differences between a child and an adult. In fact 
> it has more to do with epistemological dimensions than with bodily 
> dimensions: knowledge is hot water on wool. It shrinks time and space.
> 
> Mark Z. Danielewski - The House of Leaves
 
The miracle of our minds provides us with the faculties to explore, imagine,
and--if only to a slight degree--even comprehend the vastness of the universe.




## Table of Contents
This table of contents should reduce the time it takes to navigate this page.
* [Tech Stack](#tech-stack)
* [Shortcodes](#shortcodes)
    * [Desmos Shortcode](#desmos-shortcode)
    * [Plotly Shortcode](#plotly-shortcode)
* [Conventions](#conventions)
    * [Desmos API Conventions](#desmos-api-conventions)
    * [Filenaming Conventions](#filenaming-conventions)
    * [Processing Conventions](#processing-conventions)




## Tech Stack
*   [Hugo: Static Site Generator](https://gohugo.io/)
*   [Cupper Theme][Cupper Theme]
*   [Katex](https://katex.org/)
*   [Processing](https://processing.org/)/[Processing.js](http://processingjs.org/)
*   [Desmos Graphing API (Hopefully)](https://www.desmos.com/api/v1.4/docs/index.html)




## Shortcodes 
In addition to those provided by the [Cupper Theme][Cupper Theme] Apple Pie
Physics adds some shortcodes for plotting via [Desmos][Desmos] or 
[Plotly JS][Plotly JS].


#### Desmos Shortcode
Has the following named parameters:

###### id (required)
By convention should be of the form `dcg-<graphName>`. 
This naming scheme ensures that it is easy to select all
desmos elements via `*[class^="dcg-"]` in your CSS.

###### width (optional)
width attribute of the graph. Defaults to `width: 100%;`.

###### height (optional)
height attribute of the graph. Defaults to `height: 400px;`.


#### Plotly Shortcode
Has the following named parameters:

###### id (required)
By convention should be of the form `dcg-<graphName>`. 
This naming scheme ensures that it is easy to select all
desmos elements via `*[class^="dcg-"]` in your CSS.

###### width (optional)
width attribute of the graph. Defaults to `width: 100%;`.

###### height (optional)
height attribute of the graph. Defaults to `height: 100%;`.




## Conventions
Rules schmules, but organization matters.


#### Desmos API Conventions
In a lot of your lessons you'll find yourself wanting to build up to an idea
over several graphs. In order to prevent yourself from repeating code, it's
better to store [Desmos Options][Desmos Options] and 
[Desmos Expressions][Desmos Expressions] in a JavaScript object so they can be
accessed and reused later.

1.  Desmos graphs should have an html id of the form `dcg-<graphName>`. 

2.  The corresponding JavaScript object that contains the information needed to
    generate the graph should have a name of the form `dcg<GraphName>`. This
    object should have the following properties:

    *   `elt`:      div that will contain the graph.
    *   `opts`:     [Desmos options][Desmos Options]. 
    *   `exprs`:    [Desmos expressions][Desmos Expressions.]

Here's an example which implements these conventions:
```html5
{{< desmos id="dcg-graph1" >}}
<script>
  var dcgGraph1 = {
    elt: document.getElementById('dcg-graph1'),
    opts: { 
      expressions: false,
      xAxisLabel: 'Time',
      yAxisLabel: 'Acceleration',
    },
    exprs: [
      {id:'dcg-a', latex:'a(t) = a_0 \\left\\{0<t\\right\\}', lineStyle: Desmos.Styles.DOTTED, secret: true},
      {id:'dcg-slider-a_0', latex:'a_0=1', sliderBounds: {min: 0, max: 5, step: 1}, secret: true},
    ],
  }
  var calculator = Desmos.GraphingCalculator(dcgGraph1.elt, dcgGraph1.opts);
  calculator.setExpressions(dcgGraph1.exprs);
</script>
{{< /desmos >}}
```

More information about the Desmos API can be found at the
[Desmos API Docs][Desmos API Docs].


### Filenaming Conventions
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



[Cupper Theme]: https://themes.gohugo.io/cupper-hugo-theme/
[Desmos]: https://www.desmos.com/
[Desmos API Docs]: https://www.desmos.com/api/v1.4/docs/index.html
[Desmos Expressions]: https://www.desmos.com/api/v1.4/docs/index.html#document-expressions
[Desmos Options]: https://www.desmos.com/api/v1.4/docs/index.html#document-calculator
[Plotly JS]: https://plot.ly/javascript/
