---
layout: post
title: The mathematical search for work
description: With Vector Calculus 👀
mathjax: true
series: true
seriesname: Energy
part: 3
image:
  path: /images/
  background: prime-bg.jpg
  feature: WorkVectorCalc/feature.svg
  credit: Me!
date: 2021-08-21
---

Jeez, it's been a while. Where have I been? Well, on this planet of course! But seriously, it's just been difficult with all kinds of things in *life*.

Aaand with that, *slightly-philosophical-Sid*'s out. Let's get started with this. What's this? This is more of a mathematical continuation to what we came up with in the last Energy Series talk. This is trying to make even more mathematical sense of the definition of work - building from the intuition we've cultivated so far.

> While this post is part of the series, I don't require you to read the last post (it wouldn't hurt to read it though :P); All you need to get going is to know what work is and how we calculate it on an elementary level.

Before we start, I should make you aware that this requires some mathematical background I'm gonna assume:

- Preliminary knowledge about vectors
- Some knowledge of calculus (especially integration for this one)

> If you aren't confident about these topics, I'd suggest you to cover them first and then continue with this. This post in the series is an *advanced-math-digression* and if you want, you can skip it.

- **For people who read the last post**, this post aims to elaborate on the last integral - we concluded with an expression for work if the force was variable and if force was a function of displacement. There's a lot to that expression and discussing it then and there wouldn't have done justice to the topic. This post targets questions like:

  - What does it mean to have the limits as two vectors? (**Hint:** It signifies that we integrate from the initial position to the final position)
  - Why vectors in there, and how do we even start coupling that with calculus?

  And I also fix the notation side of things a tad bit to make it fit with calculus (The $$s$$ in the feature image represents arc length not displacement!)

- **For people who didn't read the last post**, no worries! You can definitely do it later. All you need to know is the stuff I assume you know. We're trying generalize the notion of work equals scalar product of force and displacement.

You see, sometimes we might not be given the force as a function of displacement, and the path the object in concern traverses along might not be straight. This problem, as we'll see, introduces us to **line integrals**.

The last post wasn't really meant to introduce the line integral either. I just wanted to add the term in to make you feel super cool about learning something.

Our aim: Find the most general expression for the work done by some *Vector Field* $$F$$ on some particle following a *path* $$C$$. We'll make sense of this statement as we cover the prerequisites.

> While this post will mainly focus on stuff in 2D, you can extend all of what is discussed here to higher dimensions because we will primarily work with vectors.
>
> We'll be assuming smooth curves throughout this post.

# Vector Field wha...?

Seems like a daunting word. Let's see if we can make sense of yet another *whateverness* people have come up with!

> A vector field is an assignment of a vector to each point in a subset of space.

Let's look at at the plot of a simple function $$y = f(x) = x^2$$. The way I've written (or well typed) it, I mean to plot the resultant value along the y-axis and get the dependent variables on the x-axis. The plot looks like so:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/xsquared.svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

Hmmm not so interesting. Just a function plot right? Well yes, but no. Yes because yep it's a function plot; no because there's more to it. Let's try to look at this in another way - think of the $$x$$-axis only. In that viewpoint, a function would be nothing but the assignment of a value to each and every point in 1 dimensional space:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/xsquared_scalarfield.svg" data-zoomable>
</center>
</p>

> The thing is continuous, but I can only **point** out so many points! (Intentional Pun)

This is very close to the definition of a vector field, but the thing is we assign a number instead of a vector to each point. We assign what is known as a *scalar*. These fields are thus called *Scalar Fields*.

> The function we talked about is not a scalar field if we look at the plot in 2D - we just have a collection of points $$(x, y)$$ in that case. In 1 dimensional space we assign a value to each point on the number line: each point is just a 1-tuple $$(x)$$ and we assign a value $$x^2$$ to that point.

Similarly, we could also look at the $$f(x, y) = x^2 + y^2$$ (this forms a paraboloid if you look at the 3 dimensional plot of $$z = x^2 + y^2$$) as a scalar field (we visualize the scalar field with a heatmap in this case):

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/scalarheatmap.svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

Extending this intuition to vectors should be fairly easy. All we need to do is assign a vector to each point in space. Why would we even need this? There are a lot of practical uses. We could, for example, describe fluid flow using these. The vectors at each point would tell us how the fluid moves and at what rate.

We could *plot* such a field by drawing an arrow at each point - the length of this arrow would correspond to the magnitude of the vector associated to that point, and the direction this arrow points to would be the direction of the vector.

> A vector field is a special case of a *vector valued function* where the *number of inputs* matches the *number of components* of the output vector.

## Let's get quivering

Alright enough intro to vector fields. Let's finally look at them in action. We'll start with a very simple vector field:

$$\vec{f}(x, y) = 4\hat{i} + 4\hat{j} = \langle4, 4\rangle$$

What this says is that the vector assigned to any point $$(x, y)$$ is going to be oriented such that it's 4 units in the positive x direction and 4 units in the positive y direction. I am going to stick to the $$\langle\dots\rangle$$ notation for the rest of this post.

The vector field would look like so:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/vectorfield(4, 4).svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

As we expected. It's already clear that such a plot is going to get super messy due to the plethora of arrows. Because of this, we usually do not capture the magnitude and *normalize* the arrows:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/vectorfield(4, 4)_normalized.svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

So we **rescale** the arrows such that their length lies between $$0$$ and $$1$$ (this is easily done by dividing the origin vector field expression by the magnitude of the vector).

> While the vector field plot thingmajig above doesn't capture the length/magnitude, we can still do so by assigning different colors to each arrow depending on the magnitude. Sounds like we merged heatmaps and vector fields!

That vector field was too simple for the likes of people like us 👀. Let's explore a better vector field:

$$\vec{f}(x, y) = \langle x, y \rangle$$

What's that? You want a plot?

No plots for you until you figure out what the plot should look like by yourself!

Alright, fine. I'll help you out:

- **Intuitive Explanation:**
  For each point $$(x, y)$$, we go $$x$$ units in the horizontal direction and $$y$$ units in the vertical direction. This means that the vector is going to be oriented the same way the point is going to be oriented: the vector is going to be oriented at the angle you need to traverse (starting from the positive $$x$$-axis) to get to the *line* the point lies in (this line also passes through the origin). In other words, for each point the arrow must point **directly outwards**.

  > $$\langle x, y\rangle$$ represents the position vector of the point $$(x, y)$$, so the vector that the vector field gives at a point is the same as the position vector of that point just moved to have its tail on the point itself instead of the origin.

- **Mathemagical Explanation**

  > Yep, I will definitely make **mathemagical** a word (at least a colloquial word).

  A point in 2D space can be described in terms of a *radius* $$r$$ and an *angle* $$\theta$$:

  $$x = r\cos(\theta) \qquad y = r\sin(\theta) \qquad 0 \leq \theta < 2\pi$$

  This means that we can write our vector field like so:
  
  $$\vec{f}(r, \theta) = r\langle \cos(\theta), \sin(\theta)\rangle$$

  The angle $$\phi$$ from the positive x-axis any vector would be oriented at is thus given by
  
  $$\tan(\phi) = \frac{r\sin(\theta)}{r\cos(\theta)} = \tan(\theta)$$
  
  This means that the vector is always going to be oriented along the line segment from the origin to the point. Hold up! That's nothing but the radius! This is why this vector field is called a **radial** vector field as it always goes along the radius.

If you understood why we expect what we expect, you've earned the plot:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/vectorfield(x, y).svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

And the cleaner, normalized version:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/vectorfield(x, y)_normalized.svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

Enough with the vector fields. I think we get the point now. With that construct developed, let's move on to the other one!

# What path?

A path is simply a route undertaken by something. We're not really worried about the *something* here, so we won't be talking about that. However, we most definitely care about the path and would like to ~~mathematically~~ mathemagically describe it.

- At *any instant*, a path has a direction, so it makes sense to describe a path with vectors.

- A path is inherently made of points, so the vectors could correspond to the position vector of a point on the path.

To satisfy the above requirements, we could have a function which would give us a **position vector** (with respect to our origin of course) given some parameter. Since we were talking about *instants*, we might as well use $$t$$ (for time) as the parameter:

$$\mathrm{Path:} \, \vec{r}(t)$$

> The choice of $$t$$ as a parameter is completely arbitrary. You can choose whatever parameter you think looks good.

Since our path has to *start* and *end*, we need to limit our parameter to a certain interval:

$$a \leq t \leq b \quad \mathrm{or} \quad t \in [a, b]$$

So in general, we need a definition of a position vector function $$\vec{r}(t)$$ and some interval to *limit* our parameter to define a path. So what are we waiting for? Let's define a path!

> A simple path has just one degree of freedom. This means that we need just one parameter to describe it.

Let's start simple - we want to describe a path that goes along the x-axis starting at the origin and ending at $$x=5$$.

In terms of position vectors, the position vector of each point on this path is $$\langle x, 0\rangle$$.

Technically speaking, we can use $$x$$ as the parameter here and we'll be done, but let's be consistent and go with $$t$$, so $$x = t$$ and $$0 \leq t \leq 5$$. Our path is thus:

$$\vec{r}(t) = \langle t, 0 \rangle \qquad 0 \leq t \leq 5$$

Let's step it up! We want to describe the path along the line $$x = y+2$$ starting at $$(-2, -4)$$ and ending at $$(6, 4)$$. Something like this:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/line_path.svg" style="border-radius: 10px" data-zoomable>
</center>
</p>

This should be easily to deal with as well. Like before, we'll choose $$x = t$$. Since $$y = x - 2$$, we have $$y = t-2$$. $$t$$ starts at $$-2$$ and ends at $$6$$, so

$$\vec{r}(t) = \langle t, t-2\rangle \qquad -2 \leq t \leq 6$$

Too easy? Are you up for a challenge? Define the path undertaken when you move along the unit circle (counterclockwise) starting from the positive x-axis (so $$(1, 0)$$) such that we end up where we started.

> Because this path ends where it starts from, it's called a **closed path**.

This one's a homework. I'll show you the result:

$$\vec{r}(t) = \langle \cos(t), \sin(t) \rangle \qquad 0 \leq t \leq 2\pi$$

Let's denote this path with $$C$$. Then $$-C$$ denotes the same path but traversed in the opposite direction. So we want to move clockwise in this case. This means that we want the input to the two trig functions to be $$2\pi$$ when $$t = 0$$ and $$0$$ when $$t = 2\pi$$. This can be done if we replace $$t$$ with $$2\pi + 0 - t$$:

$$-C: \, \vec{r}(t) = \langle \cos(2\pi - t), \sin(2\pi - t) \rangle = \langle \cos(t), -\sin(t) \rangle \qquad 0 \leq t \leq 2\pi$$

Where the last equality stems from some simple trig function properties.

> In general, if a path $$C$$ is described by $$\vec{r}(t)$$ where $$a\leq t \leq b$$ then $$-C$$ is described by $$\vec{r}(b+a-t)$$. I'll leave it to you to figure out why.

The initial goal should make even more sense now:

*We want to develop an expression for the work done by a force (described by a vector field $$\vec{F}$$) on a particle moving along a path ($$C$$).*

So without any further ado, let's *work* on finding work!

> Sid: The Pun God

# Work!

Let's work with what we have so far. Imagine a force described by a vector field. And imagine some path $$C$$. Can't imagine? Here, this image will help:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/work_1.svg" data-zoomable>
</center>
</p>

The orange arrows denote the vector field we were talking about. The green curve is our path $$C$$ and the arrows on it signify the direction of our path. We need to find the work done by the force as something goes along this path. This task seems pretty daunting at first, but let's do the best we can.

Let's focus on one section. To find the work done by the force along the path, we only need to account for the contribution along the path. This necessitates to find the component along the path (**tangent** to it). This can be done if we find an expression for the (unit) tangent vector to the path and utilize the scalar product:

$$F_\text{along the path} = \vec{F}\cdot \vec{T}$$

Notice that we only care about the magnitude of this force and not its direction once we have it resolved. This should be obvious since we already have the direction feature captured in the tangent vector. The component along the direction of motion is the only component that does work, so there's no need for an inherent direction once we have the component.

> This tangent vector **needs** to be a unit vector because we only want the unscaled magnitude of the component. So we'll call it the **unit tangent vector**.

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/work_2.svg" data-zoomable>
</center>
</p>

Well, this is all fine, but this just delegates our task; We now need to find the expression for the unit tangent vector. Oh and we also need to find the small length this force applies to!

Both of these seem like properties of the path itself. The tangent vector task seems relatively easy, so let's tackle that first.

## Tangent Adventures

- Intuition 1: We know that for a function $$y = f(x)$$ the slope of the tangent line is given by the derivative of $$f(x)$$. Perhaps the tangent vector has to do something with derivatives?
- Intuition 2: We want the tangent vector because we need to capture the direction. Our path is nothing but a collection of position vectors. Is there a way to get a direction given two position vectors? Oh yes of course! Let's say we have two points $$A$$ and $$B$$ with position vectors $$\vec{a}$$ and $$\vec{b}$$ respectively. The difference
  
  $$\vec{b} - \vec{a}$$

  can be interpreted geometrically as the direction of the path from $$A$$ to $$B$$!

  <p>
  <center>
    <img src="/blog/images/WorkVectorCalc/work_3.svg" style="height: 250px" data-zoomable>
  </center>
  </p>

Okay, let's find the direction for the small section. At the point of concern, the position vector will be $$\vec{r}(t)$$ for some $$t$$. Because our path is *parametrized* by $$t$$, we can increase this $$t$$ by a small amount $$\Delta t$$ to consider a nearby position vector. This position vector would be $$\vec{r}(t + \Delta t)$$. The difference of these two vectors will give us the direction:

<p>
  <center>
    <img src="/blog/images/WorkVectorCalc/work_4.svg" data-zoomable>
  </center>
</p>

Hmmm. How do we proceed now? We don't really have a certain value for this $$\Delta t$$, so what do we do? Hey! If we divide the difference by $$\Delta t$$, we get the vector

$$\frac{\vec{r}(t + \Delta t) - \vec{r}(t)}{\Delta t}$$

which is awfully similar to the definition of a derivative. The only thing different is that we have vectors. Can we get around that somehow? Notice that the path $$\vec{r}(t)$$ is itself a vector of functions. So we could write it like so:

$$\vec{r}(t) = \langle x(t), y(t)\rangle$$

> I am just considering the 2 dimensional case, but you can extend the thing above to other dimensions. For example, in 3 dimensions we have
> $$\vec{r}(t) = \langle x(t), y(t), z(t) \rangle$$
> and so on.

So we could rewrite our previous expression like so:

$$\frac{\vec{r}(t + \Delta t) - \vec{r}(t)}{\Delta t} = \bigg\langle\frac{x(t + \Delta t) - x(t)}{\Delta t}, \frac{y(t + \Delta t) - y(t)}{\Delta t}\bigg\rangle$$

The fractions on the left hand side are simply derivatives when we consider the limit as $$\Delta t \to 0$$. This lets us eliminate $$\Delta t$$ (in a way). So, we can form a new vector $$\vec{r}'(t)$$, and define it like so

$$\vec{r}'(t) = \langle x'(t), y'(t) \rangle$$

This vector is definitely tangent to the path and can be found out for any $$t$$. Isn't it cool that both of our intuitions had to be merged to get the tangent vector?

We're still not done with the *tangent adventures*. We need the tangent vector to be normalized so that the magnitude is $$1$$. Therefore, we define the unit tangent vector like so:

$$\vec{T} = \frac{\vec{r}'(t)}{\left\Vert \vec{r}'(t) \right\Vert}$$

> This of course assumes $$\left\Vert \vec{r}'(t) \right\Vert \neq 0$$

where $$\left\Vert \vec{r}'(t) \right\Vert$$ denotes the norm/magnitude of our vector quantity and could also be written as

$$\left\Vert \vec{r}'(t) \right\Vert = \sqrt{x'(t)^2 + y'(t)^2}$$

## The length emprise

Alright, the last puzzle in the box: the small length. This should be fairly easy to find if we consider the changes in $$x$$ and $$y$$ and then apply Pythagoras' Theorem:

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/work_5.svg" data-zoomable>
</center>
</p>

How is this fairly easy? We still have the $$\Delta t$$ lingering. Well, not really; we'll do something similar to what we did before:

$$\begin{aligned}
  \Delta s &= \sqrt{(\Delta x)^2 + (\Delta y)^2} \\
           &= \frac{\sqrt{(\Delta x)^2 + (\Delta y)^2}}{\Delta t} \cdot \Delta t\\
           &= \sqrt{\left( \frac{\Delta x}{\Delta t} \right)^2 + \left( \frac{\Delta y}{\Delta t} \right)^2} \cdot \Delta t\\
\end{aligned}$$

When we consider the limit as $$\Delta t \to 0$$, the quotients turn to derivatives, and the differences ($$\Delta \dots$$) turn to differentials ($$\mathrm{d}\dots$$). Hence,

$$\mathrm{d}s = \sqrt{x'(t)^2 + y'(t)^2}\, \mathrm{d}t$$

Hold up! That radical term is exactly equal to $$\left\Vert \vec{r}'(t) \right\Vert$$! This should make sense - we would want the length corresponding to the difference in the positions. Therefore,

$$\mathrm{d}s = \left\Vert \vec{r}'(t) \right\Vert\, \mathrm{d}t$$

This expression can be extended to higher dimensions.

> Just like we hypothesized, both the tangent vector and the length are features of the path itself!

This infinitesimal length is all we need for the infinitesimal work that as done for this small section. However, before we get to the expression, we need to go through a small yet essential digression.

## The difference between this length and displacement

Displacement is inherently a vector quantity. The infinitesimal length, however, is a scalar quantity - it doesn't capture the notion of a direction.

This length is very related to the **arc length** of a curve. The arc length is the distance between two points as we go along the curve. As we found out before, the arc length between two very close points is

$$\mathrm{d}s = \left\Vert \vec{r}'(t) \right\Vert\, \mathrm{d}t$$

We can integrate this to get the arc length between two points:

$$s = \int_{t_0}^{t_1}\left\Vert \vec{r}'(t) \right\Vert\, \mathrm{d}t$$

For example, if we were to calculate the perimeter of a circle, we can make use of our parametrization from before:

$$\begin{aligned}
  \vec{r}(t) &= \langle \cos(t), \sin(t) \rangle \qquad 0 \leq t \leq 2\pi \\ 
  \implies \left\Vert \vec{r}'(t) \right\Vert &= \sqrt{(-\sin(t))^2+ (\cos(t))^2} = 1
\end{aligned}$$

Therefore, the perimeter of the circle would be:

$$\int_0^{2\pi} 1 \,\mathrm{d}t = 2\pi$$

Just as we expect!

We can also define an arc length function which gives us the arc length from a particular point to a point associated to some $$t$$:

$$s(t) = \int_{a}^{t}\left\Vert \vec{r}'(u) \right\Vert\, \mathrm{d}u$$

> I changed the variable from $$t$$ to $$u$$ to make differentiating stuff easier for you.

So what's the displacement then? The displacement is the difference between the two position vectors. Fairly obvious, no? What else do I have set up for you in this moment of truth? Well, the infinitesimal displacement is actually $$\mathrm{d}\vec{r}$$:

$$\frac{\mathrm{d}\vec{r}}{\mathrm{d}t} = \vec{r}'(t) \implies \mathrm{d}\vec{r} = \vec{r}'(t)\,\mathrm{d}t$$

This means that if $$\vec{r}(t) = \langle x(t), y(t) \rangle$$, $$\mathrm{d}\vec{r}$$ could also be written as

$$\mathrm{d}\vec{r} = \vec{r}'(t)\,\mathrm{d}t = \langle x'(t), y'(t) \rangle\, \mathrm{d}t$$

We can shorten this down further by realizing that $$\mathrm{d}x = x'(t)\,\mathrm{d}t$$ and $$\mathrm{d}y = y'(t)\,\mathrm{d}t$$:

$$\mathrm{d}\vec{r} = \langle x'(t), y'(t) \rangle \,\mathrm{d}t = \langle \mathrm{d}x, \mathrm{d}y\rangle$$

Pretty cool! Oh and remember the unit tangent vector? Well here's the expression:

$$\vec{T} = \frac{\vec{r}'(t)}{\left\Vert \vec{r}'(t) \right\Vert}$$

The denominator is nothing but $$\frac{\mathrm{d}s}{\mathrm{d}t}$$:

$$\vec{T} = \vec{r}'(t)\cdot \frac1{\frac{\mathrm{d}s}{\mathrm{d}t}} = \frac{\mathrm{d}\vec{r}}{\mathrm{d}t} \cdot \frac1{\frac{\mathrm{d}s}{\mathrm{d}t}} = \frac{\mathrm{d}\vec{r}}{\mathrm{d}s}$$

That's another cool expression in our box!

## Connecting the dots

Alright, enough rambling about. We have all the expressions we need. Let's *integrate* all of these into one *integral* expression.

> Yeah, I think that's enough puns for a post.

We devised expressions for the force tangent to the path, and the infinitesimal length. We can combine these to get the infinitesimal work done:

$$\mathrm{d}W = \vec{F}\cdot \vec{T} \mathrm{d}s$$

Integrating this from $$0$$ arc length all the way to the full arc length covers the whole path:

$$W = \int_0^W\mathrm{d}W = \int_0^s\vec{F}\cdot \vec{T}\, \mathrm{d}s$$

This. This integral is the integral we were after. This is called the line integral. Now I would say we could've done justice to the concept and called it the path integral instead, but 🤷

This integral has a special name solely because we integrate along the path instead of some simple straight line.

> The fact that this is a line integral is usually emphasized by writing $$C$$ under the integral symbol - like I did in the feature image.

Notice that we can only make direct use of the above integral when the force is parametrized in terms of the arc length. In all of our parametrizations, we did it with $$t$$ instead, so it makes sense to try to find an expression in terms of that. In fact, we can do that! Recall from our digression that

$$\vec{T} = \frac{\mathrm{d}\vec{r}}{\mathrm{d}s}$$

Therefore we can rewrite the integral:

$$W = \int_{\vec{r}_0}^{\vec{r}_1}\vec{F}\cdot \mathrm{d}\vec{r}$$

This is still not in terms of $$t$$, but before we move on, notice that this is the expression we came up with in the last post. Knowing all of the peculiarities makes it more appreciable (for me, at least). In the last post $$s$$ took the place of $$r$$, but here we need it for the arc length. This is an intermediate expression.

If our path is parametrized in terms of $$t$$, then $$\mathrm{d}\vec{r} = \vec{r}'(t)\,\mathrm{d}t$$ as we saw before. So,

$$W = \int_{t=a}^{t=b}\vec{F}(t)\cdot \vec{r}'(t)\,\mathrm{d}t$$

This is the most useful and simple-to-use expression. It also captures the fact that we define the path by limiting $$t$$ to an interval, so that's pretty good.

# Let's use what we learned!

This was a ridiculously complex topic to cover, and to ensure that you get all of it, you might wanna read some parts again. In addition to that, we'll apply what we learned to **find the work done by the force $$\vec{F} = \langle x, y \rangle$$ on something that moves along the unit circle (counterclockwise, starting from the positive x-axis).**

The path is something we already parametrized before (in our homework):

$$\vec{r}(t) = \langle \cos(t), \sin(t) \rangle \qquad 0 \leq t \leq 2\pi$$
$$\vec{r}'(t) = \langle -\sin(t), \cos(t) \rangle$$

Our aim is to find the work done using the two expressions in the order that they appeared.

<p>
<center>
  <img src="/blog/images/WorkVectorCalc/work_6.svg" data-zoomable>
</center>
</p>

As we can see from the figure, the work we should get must be $$0$$ since the force is perpendicular to the direction of motion all the way.

> The names I am giving to the expressions aren't the official names, but I think they do the job fairly well.

## The arc length expression

$$W = \int_0^s\vec{F}\cdot \vec{T}\,\mathrm{d}s$$

- Since we're going around the whole unit circle, the full arc length is $$s = 2\pi$$.
- We need to reparametrize the path in terms of the arc length. This means we need a relation between $$s$$ and $$t$$. We know that
  
  $$s(t) = \int_{a}^{t}\left\Vert \vec{r}'(u) \right\Vert\, \mathrm{d}u$$

  In our case it makes sense to take $$a=0$$ because we're talking about the whole circle. Therefore,

  $$\begin{aligned}
    s(t) &= \int_0^t \left\Vert \vec{r}'(u) \right\Vert\, \mathrm{d}u \\
         &= \int_0^t \sqrt{\sin^2(u) + \cos^2(u)}\mathrm{d}u \\
         &= \int_0^t \mathrm{d}u \\
         &= t
  \end{aligned}$$

  So $$s = t$$. How convenient!

  This means our path $$C$$ is

  $$\vec{r}(s) = \langle \cos(s), \sin(s) \rangle \qquad 0 \leq s \leq 2\pi$$

  And our force would be defined like so:

  $$\vec{F} = \langle x, y \rangle = \langle x(s), y(s) \rangle = \langle \cos(s), \sin(s) \rangle$$

- The unit tangent vector is going to be
  
  $$\vec{T} = \frac{\vec{r}'(s)}{\left\Vert \vec{r}'(s) \right\Vert} = \frac{\langle -\sin(s), \cos(s) \rangle}{1} = \langle -\sin(s), \cos(s) \rangle$$

- Therefore, the work done is:

  $$W = \int_0^{2\pi} \langle \cos(s), \sin(s) \rangle \cdot \langle -\sin(s), \cos(s) \rangle \, \mathrm{d}s = 0$$

  As we expected.

## The $$t$$ equation

- Because $$s = t$$, the integrals must be the same. So,

  $$W = \int_0^{2\pi} \langle \cos(t), \sin(t) \rangle \cdot \langle -\sin(t), \cos(t) \rangle \, \mathrm{d}t = 0$$

# Thank You!

Phew! That was a lot! If you're reading this, thanks a bunch for sticking around. This was a long one, and I don't expect you to read it all in one go. I am not sure how many people read my blog posts and for how long, but it does mean a lot if you've read this far because this took a lot of *work* (alright that's the last pun I promise).

In conclusion,

$$W = \int_C \vec{F}\cdot \vec{T}\, \mathrm{d}s = \int_C \vec{F}\cdot\mathrm{d}\vec{r} = \int_C \vec{F}(t)\cdot\vec{r}'(t)\,\mathrm{d}t$$

I hope I could help you learn something new. I'll see you soon (hopefully)!
