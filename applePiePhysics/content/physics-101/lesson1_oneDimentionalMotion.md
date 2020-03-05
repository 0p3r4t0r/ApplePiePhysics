---
title: "Motion in One Dimension"
weight: 2
draft: false
---
## A Mysterious Space Train
One day we discovered a train traveling through the vast emptiness of space at
at low speed. No one knows where it came from and no one knows where 
it's going. We've sent a team of scientists to find out more about the train
and you've they've been living on board for several weeks now.

As far as everyone can tell **the velocity of the train is constant** and 
**the track along which the train travels is perfectly straight**. You have 
been recording the position of the train for a number of weeks now, but you're 
starting to run out of space in your notebook.

*You need a concise way of describing where the train is and
where the train is going to be.*




## Describing the Train's Motion
Since the train travels in a straight line, we know it's only moving in one
direction. Let's call that direction \\( p \\).
If we call the time and place we started to observe the train \\( t_0 \\) and
\\( p_0 \\) respectively we can write the initial position of our train as
. . . 

\\[
p(t_0) = p_0 \tag{1.1}
\\]

So equation 1.1 simply expresses the idea that the position \\( (p) \\) at the
time when we started \\( (t_0) \\) is equal to the position where we first
found the train \\( ( p_0 ) \\).


Now as time goes on the distance from our starting point increases. Since our
train is moving at a constant velocity \\( (v_0) \\), the distance it travels 
\\( (d) \\) as funciton of time \\( (t) \\) can be written as ...

\\[
d(t) = v_0t \tag{1.2}
\\]

Then the position of the train across time must be wherever it started 
*plus its distance from that point as a function of time.* Combining 
equations 1.1 and 1.2 leads us to equation 1.3 below.

\\[
p(t) = p_0 + v_0 t \tag{1.3}
\\]

Suddenly we notice that the velocity of the train has started to change. It
feels as if the train has begun to accelerate ever so slightly! Unfortunately, 
we were so engrossed in our thoughts earlier that we failed to notice the 
change in velocity for several minutes and it seems the other scientists were 
too busy contemplating the meaning of the train to have noticed themselves.

Our instruments can tell us the *current* velocity of the train and we know 
that velocity as a funciton of time is given by . . .

\\[
v(t) = v_0 + a_0t \tag{1.4}
\\]

Although information about the train's velocity from moment-to-moment is 
forever lost to our neglegence, we can at least try to update equation 1.3
to use the *average velocity* of the train \\( (\overline{v}) \\) instead
of its *initial velocity* \\( (v_0) \\). 

Mathematically speaking we want to replace 1.3 with 1.5 below.

\\[
p(t) = p_0 + \overline{v}(t) \cdot t \tag{1.5}
\\]

The average velocity is equal to the average of our velocity at time \\( t \\) 
and our initial velocity.

\\[
\overline{v}(t) = \dfrac{v_0 +  v(t)}{2} \tag{1.6}
\\]

Substituting 1.4 into 1.6 yields . . .

\\[
\overline{v}(t) = \dfrac{2v_0 + a_0t}{2} \tag{1.7}
\\]

Finally plugging 1.7 back into 1.5 leads us to . . .

\\[
p(t) = p_0 + v_0 t + \dfrac{1}{2}a_0t^2 \tag{1.8}
\\]

{{% note %}}
If we set \\( a_0 = 0 \\) in equation 1.8 we are lead right back to equation
1.3. This make perfect sense because equation 1.3 represents the train's
position across time when the acceleration was zero! 
{{% /note %}}




## Verifying the 1-D Motion Equation Graphically
At the other end of the train. Another scientist has been thinking a bit
differently. She noticed the train's change in velocity at about the same time
we did, and has been carefully plotting the acceleration, velocity, and postion
of the train across time ever since. She's even taken the time to graph some of
her results. Let's see how our formula compares with some of her data ....


### Acceleration vs. Time Graph
Try and plot a curve to fit the data on the graph below. Click the 
\\( \Large{>>} \\) symbol in the top left to display the expressions.
If you're having trouble making anything appear on the graph try reading 
through the [Desmos tutorial](https://learn.desmos.com/graphing) for help.

{{< desmos id="dcg-graph1" >}}
<script>
  var dcgGraph1 = {
    elt: document.getElementById('dcg-graph1'),
    opts: { 
      expressionsCollapsed: true,
      xAxisLabel: 'Time',
      xAxisArrowMode: Desmos.AxisArrowModes.BOTH,
      yAxisLabel: 'Acceleration',
      yAxisArrowMode: Desmos.AxisArrowModes.BOTH,
      lockViewport: true,
    },
    exprs: [
      { id:'dcg-a',
        latex:'a(t) = a_0 \\left\\{0<t\\right\\}', 
        lineStyle: Desmos.Styles.DOTTED,
        secret: true,
      },
      { id:'dcg-value-a_0',
        latex:'a_0=1',
        secret: true,
      },
      // show point (t_0, a_0)
      { id: 'dcg-point-a_0',
        latex: '(0, a_0)',
        label: '`(t_0,\\ a_0)`',
        showLabel: true,
        labelSize: Desmos.LabelSizes.LARGE,
        color: Desmos.Colors.BLACK,
        secret: true,
      },
    ],
    bounds: {
      left: -1,
      right: 10,
      bottom: -1,
      top: 10,
    }
  }
  var calculator = Desmos.GraphingCalculator(dcgGraph1.elt, dcgGraph1.opts);
  calculator.setMathBounds(dcgGraph1.bounds);
  calculator.setExpressions(dcgGraph1.exprs);
</script>
{{< /desmos >}}

{{< expandable label="Solution" >}}
This data tells us that the acceleration of the train is *constant*.
Mathematically speaking that's ...

\\[ a(t) = 1 \tag{1.9} \\]
{{< /expandable >}}


### Velocity vs. Time Graph:
Now try and plot a function that will match our data for velocity (check
equation 1.4 above if you find yourself in need of some inspiration).

{{< desmos id="dcg-graph2" >}}
<script>
  var opts = dcgGraph1.opts
  opts['yAxisLabel'] = 'Velocity'
  var dcgGraph2 = {
    elt: document.getElementById('dcg-graph2'),
    opts: opts,
    exprs: [
      { id:'dcg-v',
        latex:'v(t) = v_0 + a_0t \\left\\{0<t\\right\\}',
        lineStyle: Desmos.Styles.DOTTED,
        secret: true,
      },
      { id:'dcg-value-v_0',
        latex:'v_0=1',
        secret: true,
      },
      // value for a_0
      dcgGraph1.exprs[1],
      // show point (t_0, v_0)
      { id: 'dcg-point-v_0',
        latex: '(0, v_0)',
        label: '`(t_0,\\ v_0)`',
        showLabel: true,
        labelSize: Desmos.LabelSizes.LARGE,
        color: Desmos.Colors.BLACK,
        secret: true,
      },
    ],
  }
  var calculator = Desmos.GraphingCalculator(dcgGraph2.elt, dcgGraph2.opts);
  calculator.setMathBounds(dcgGraph1.bounds);
  calculator.setExpressions(dcgGraph2.exprs);
</script>
{{< /desmos >}}

{{< expandable label="Solution" >}}
From this graph we can read off our initial velocity \\( (v_0) \\) and use
the acceleration data from the graph above to reconstruct equation 1.4. 

\\[ 
  v(t) = 1 + 1 \cdot t \tag{1.10}
\\]
{{< /expandable >}}


### Position vs. Time Graph
Finally, let's bring it all together and try to fit a function to our position
data (check equation 1.8 if you get stuck). 

{{< desmos id="dcg-graph3" >}}
<script>
  var opts = dcgGraph1.opts
  opts['yAxisLabel'] = 'Position'
  var dcgGraph3 = {
    elt: document.getElementById('dcg-graph3'),
    opts: opts,
    exprs: [ 
      { id:'dcg-p',
        latex:'p(t) = p_0 + v_0t + \\frac{1}{2}a_0t^2 \\left\\{0<t\\right\\}', 
        lineStyle: Desmos.Styles.DOTTED, 
        secret: true,
      },
      { id:'dcg-value-p_0',
        latex:'p_0 = 0',
        secret: true,
      },
      // value for v_0
      dcgGraph2.exprs[1],
      // value for a_0
      dcgGraph1.exprs[1],
      // show point (t_0, p_0)
      { id: 'dcg-point-p_0',
        latex: '(0, p_0)',
        label: '`(t_0,\\ p_0)`',
        showLabel: true,
        labelSize: Desmos.LabelSizes.LARGE,
        color: Desmos.Colors.BLACK,
        secret: true,
      },
    ],
  }
  var calculator = Desmos.GraphingCalculator(dcgGraph3.elt, dcgGraph3.opts);
  calculator.setMathBounds(dcgGraph1.bounds);
  calculator.setExpressions(dcgGraph3.exprs);
</script>
{{< /desmos >}}

{{< expandable label="Solution" >}}
Finally, using this last graphs and what we already know about about 
\\( a_0 \\) and \\( v_0 \\) we can cast equation 1.8 as . . .

\\[
  p(t) = 0\ + 1\ \cdot t + \frac{1}{2} \cdot 1\ \cdot t^2 \tag{1.11}
\\]
{{< /expandable >}}




## Units
Alright, so we've managed to derive an accurate expression for the position
of the train, but an expression about distance doesn't mean much without units.
We've used three quantities with different units so far . . .

distance
:   Describes where something is relative to a given point.

velocity
:   Describes the rate of change in position with respect to time. We can
    calculate the average velocity of an object by subtracting its initial
    position \\( (p_0) \\) from its final position \\( (p_f) \\) and 
    dividing by the time in between.  

    \\[ v_{avg} = \frac{p_f - p_0}{t_f - t_0}  \tag{1.12} \\]
    

acceleration
:   Describes the rate of change in velocity with respect to time. We can
    calculate the average acceleration of an object by subtracting its initial
    velocity \\( (v_0) \\) from its final velocity \\( (v_f) \\) and dividing
    by the time in between.

    \\[ a_{avg} = \frac{v_f - v_0}{t_f - t_0} \tag{1.13} \\] 


### Unit Equations
The [SI base unit](https://en.wikipedia.org/wiki/SI_base_unit) for distance
is the meter \\( (m) \\) and the SI base unit for time is the second 
\\( (s) \\). Knowing this we can write what I like to call *unit equations*
to quickly find the appropriate units for velocity and acceleration.

We can use equation 1.12 to figure out the units for velocity.

\\[ \text{Units}(v_{avg}) = \frac{ m - m }{ s - s} = \frac{m}{s} \tag{1.14} \\]

Note that the math in equation 1.14 works a little differntly than you may
have expected. If \\( m \\) and \\( s \\) represented numbers then 1.14 would
lead us to \\( 0 / 0 \\) which is undefined. The important thing to remember
is that **\\( m \\) and \\( s \\) represent units and not numbers.**

The difference of two quantities in meters is another quantity in meters. For
example ...

\\[ 5\ m - 3\ m = 2\ m\\]

If we drop all of the numbers we are left with a *unit equation* that tells us
that 

\\[ m - m = m\\]

Now try and find the units for acceleration by working out the unit equation
that corresponds to equation 1.13.

{{< expandable label="Solution" >}}
\\[
  \text{Units}(a_{avg}) = \frac{m/s - m/s}{s - s} = \frac{m}{s^2} \tag{1.15}
\\]
{{< /expandable >}}


### Unit Check for Equation 1.8
> If your units come out wrong, then your equation is wrong. If your units 
> are right, then you *might* be right.

Let's go all the way back to equation 1.8 and make sure that the units come out
alright. With  meters \\( (m) \\) as our unit of distance and seconds
\\( (s) \\) as our unit of time the unit equation for 1.8 becomes . . .

\\[
\text{Units}(p) = m + \frac{m}{s} \cdot s + \frac{m}{s^2} \cdot s^2 = m 
\tag{1.16}
\\]

So the units of position come out in meters. Looks like we're good to go!


## Closing Remarks From the Scientists
We are now aware that the train is subject to changes in velocity. Even 
after all of the time we've spent here we were unable to glean information
about how the train moves and its inner-working remain a mystery to us.

We have noticed one thing however: the track along which the train travels
was visible in the night sky above our home planet weeks before we ever saw
the train, but now we've received a report that it has vanished. Glancing out
the window we can see the track of the train glowing beneath us and we note
that it seems to extend for vast distances in either direction. Odd as it seems
we now believe that the train creates its own track as it moves through space. 

It would be a wonder to stay on board, but alas we are short of provisions 
and have elected to head back before the train ventures any further
away from our home planet.
