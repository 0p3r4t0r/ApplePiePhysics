---
title: "Motion in One Dimension"
weight: 2
draft: true
---
## A Mysterious Space Train
One day we discovered a train traveling through the vast emptiness of space at
at low speed. No one knows where it came from and no one knows where 
it's going. We've sent a team of scientists to find out more about the train
and they've been living on board for several weeks now.

As far as we can tell <u>the velocity of the train is constant</u> and <u>the
track along which the train travels is perfectly straight</u>. Our scientists
have been recording the position of the train for a number of weeks now, 
but they're starting to run out of space in their logs.

*Our scientists need a concise way of describing where the train is and where
the train is going to be.*




## Describing the Train's Motion
Since the train travels in a straight line, we know it's only moving in one
direction. Let's call that direction \\( x \\).
If we call the time and place we started to observe the train \\( t_0 \\) and
\\( x_0 \\) respectively we can write the initial position of our train as... 

\\[
x(t_0) = x_0 \tag{1.1}
\\]

So equation 1.1 simply expressed the idea that the position \\( (x) \\) at the
time when we started \\( (t_0) \\) is equal to the position where we first
found the train \\( ( x_0 ) \\).


Now as time goes on the distance from our starting point increases. Since our
train is moving at a constant velocity \\( (v) \\), the distance it travels 
\\( (d) \\) as funciton of time \\( (t) \\) can be written as ...

\\[
d(t) = vt \tag{1.2}
\\]

Then the position of the train across time must be, wherever it was at the 
begining *plus its distance from that point.* Combining equations 1.1 and 1.2 
leads us to equation 1.3 below.

\\[
x(t) = x_0 + v_0 t \tag{1.3}
\\]

Suddenly we notice that the velocity of the train has started to change. It
feels as if the train has begun to accelerate ever so slightly! Unfortunately, 
we were so engrossed in our thoughts earlier that we failed to notice the 
change in velocity for several minutes and it seems the other scientists were 
too busy contemplating the meaning of the train to have noticed themselves.

Our instruments can tell us the *current* velocity of the train and we know 
that velocity as a funciton of time is given by ...

\\[
v(t) = v_0 + a_0t \tag{1.4}
\\]

Although information about the train's velocity from moment-to-moment is 
forever lost to our neglegence, we can at least try to update equation 1.3
to use the *average velocity* of the train \\( (\overline{v}) \\) instead
of its *initial velocity* \\( (v_0) \\). 

Mathematically speaking we want to replace 1.3 with 1.5 below.

\\[
x(t) = x_0 + \overline{v}(t) \cdot t \tag{1.5}
\\]

The average velocity is equal to the average of our velocity at time \\( t \\) 
and our initial velocity.

\\[
\overline{v}(t) = \dfrac{v_0 +  v(t)}{2} \tag{1.6}
\\]

Substituting 1.4 into 1.6 yields ...

\\[
\overline{v}(t) = \dfrac{2v_0 + a_0t}{2} \tag{1.7}
\\]

Finally plugging 1.7 back into 1.5 leads us to ...

\\[
x(t) = x_0 + v_0 t + \dfrac{1}{2}a_0t^2 \tag{1.8}
\\]

{{% note %}}
If we set \\( a_0 = 0 \\) in equation 1.8 we are lead right back to equation
1.3. This make perfect sense because equation 1.3 represents the train's
position across time when the acceleration is zero! 
{{% /note %}}




## Graphically Checking for the 1-D Motion Equation
At the other end of the train. Another scientist is thinking a little bit
differently. She's been dilligently plotting the position, velocity, and
acceleration of the train while we wittled away at our calculations.

{{% desmos %}}
<script>
  var elt = document.getElementById('calculator');
  var calculator = Desmos.GraphingCalculator(elt);
  calculator.setExpressions([
      {id:'dg-a', latex:'a(t)=a_0'},
      {id:'slider-a_0', latex:'a_0=1', sliderBounds: {min: 0, max: 5, step: 1}}
    ]);
  console.log('Here is my graph:', elt);
</script>
{{% /desmos %}}
