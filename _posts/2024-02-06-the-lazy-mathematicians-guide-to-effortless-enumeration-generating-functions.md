---
layout: post
title: The Lazy Mathematician's Guide to Effortless Enumeration
date: 2024-02-06
mathjax: true
description: "A post introducing one of the most convenient tools in the world of combinatorics and discrete mathematics: generating functions."
image:
  feature: Generating Functions/feature.svg
  credit: Me!
---

> A generating function is a very useful clothesline on which we hang up a sequence of numbers for display.

Whilst this blog is to cover things I come across or just want to talk about, it is quite often that I find myself in a position wherein I want to talk about something that needs something else. And ye olde Sid can't help but discuss said prerequisites.

One such prerequisite that opens up a lot of things in the world of math is what is known as a generating function. In this post I want to share how useful these things can be.

> If you're familiar with sequences and series, you can just skip to the generating functions bit. That being said, while I do introduce some stuff to form a coherent story, you can't be lazy with enumeration if you don't understand sequences and series. So I do assume familiarity quite a bit (with [references](#references) included so don't you worry!)

# 1 then 2 then 3 then ...?

A sequence is a bunch of numbers one after another. Quite a simple thing. Sequences are super important in math. Sequences of prime numbers, the Fibonacci sequence and tons more. In fact there's a whole online directory of sequences called [The On-Line Encyclopedia of Integer Sequences® (OEIS®)!](https://oeis.org/)

The simplest way to represent a sequence is to just talk about an arbitrary $$n^\mathrm{th}$$ term in the sequence $$a_n$$. If you have some expression for each term, then voila you basically describe the entire sequence. Say for example I wanted to talk about the natural numbers. Then we just have:

$$a_n = n \qquad (n\geq 1)$$

And then the first term is quite simply $$a_1 = 1$$, then the second term is $$a_2 = 2$$ and so on so forth. You get the point.

Quite cool! Turns out there's another way to represent sequences. Using a very nifty tool that one usually comes across during their first excursion in the lands of calculus.

# Power series

A mathematical series is a sum of a bunch (infinitely many usually when not explicitly mentioned) of things. A power series is then (loosely speaking) the sum of those bunch of things each raised to a power. If you've had any experience with Taylor series or convergence when studying Calculus you should already know what I am talking about. Let's turn this intuition into a *mathemagical*{:.tooltip data-tooltip="And you thought I would forget about the word I have been hyping up across all my posts"} definition:

Given an infinite (we love eternal things) sequence $$a_n$$, its corresponding series is 

$$
\sum_{i=1}^\infty a_i
$$

A power series is again, a sum of a bunch of things, but it's more like a series with a function (a polynomial in this case because we'll be raising things to a power) in there. The most general form goes:

$$
\sum_{n=0}^\infty a_n (x-x_0)^n
$$

One of the more popular series is the Taylor series. This can help approximate a function using derivatives (it is exact in the infinite limit). As an example, the Taylor series of $$\sin(x)$$ centered at $$x_0 = 0$$ takes the form

$$
\sum_{n=0}^\infty \frac{(-1)^n}{(2n+1)!} x^{2n+1}
$$

Notice how we have $$x$$ *raised to some power*. In this case only odd powers exist, but this can be reframed to say that the even powers have a coefficient of $$0$$ which is why they don't seem to appear. This point of view is what I'd like you to keep: Pay attention to the coefficients more than the $$x^{\dots}$$ terms.

## Alright let's get formal

So far when I've said *sum* you've probably interpreted it as an evaluation of a lot of additions. And that is absolutely correct, but here's another way to think about this: forget that their is some addition, and just focus on the coefficients of each term. Why though? That way instead of thinking that we need to evaluate *some sum*{:.tooltip data-tooltip="Does that qualify as a rudimentary pun?"} and have that as the value, we think about each of the coefficients being a placeholder for any number we want. 

This is called a formal power series. Looks like a power series, will usually behave like a power series, but we're more worried about the coefficients that appear. Why would one want to do so? Well because power series are easier to handle; many of them have alternative expressions, the algebra just works out well for us, things make sense, and we're lazy (okay you're not).

# Generating Functions!

A generating function is a formal power series with the sum not being the focal point but rather the order in which the coefficients appear - to define a sequence!

Okay since our first sequence was just $$1, 2, 3, \dots$$, let's try to represent that using a generating function. We know our general term is $$a_n = n$$, and so the generating function is 

$$
A(x) = \sum_{n=0}^\infty n x^n
$$

What we'd even want to do with this is not completely obvious, so I am going to start with a very very very simple sequence. The infinite sequence of $$1$$s: $$a_n = 1$$. 

The generating function for this would be:

$$
A(x) = \sum_{n=0}^\infty 1\cdot x^n = \sum_{n=0}^\infty x^n
$$

If you're familiar with the geometric series (see [Geometric Series -- from Wolfram MathWorld](https://mathworld.wolfram.com/GeometricSeries.html)), then you will know that the last sum is essentially an infinite geometric series and it is equivalent to $$\frac{1}{1-x}$$. There are convergence issues ($$\lvert x\rvert$$ has to be less than $$1$$), but since we don't bother with what the actual evaluated value is, we can use this to sneakily represent  all the terms of our (arguably not so useful) sequence!

It doesn't have to be crazy infinities either! Say for example you wanted to represent the sequence $$0, 2$$. Then the generating function is just $$2x$$. That's great and all, but does this have any significance? So far  we haven't really seen any breakthroughs that would make us appreciate this. And I promise the "aha!"s will keep coming.

## Example 1

We can tack on more powers of $$2$$ to the sequence to get $$0, 2, 4, \dots$$. The $$n^\mathrm{th}$$ term essentially represents the number of binary numbers you'd have if you had $$n$$ bits to spare. The generating function for this will be $$\frac{1}{1-2x}$$. No other work needed. And as soon as you look at the generating function you can just go "Oh it's a formal representation of the geometric series with common ratio $$2x$$" So the coefficient of $$x^n$$ is just $$2^n$$.

## Example 2

Say I had a normal $$6$$-sided die and I wanted to know the number of ways of it landing on a face. The $$n^\mathrm{th}$$ term of the sequence would tell us the number of ways of getting $$n$$. This is clearly just a bunch of $$1$$s. Six 1s to be precise. The generating function for that would be 

$$
x+x^2+x^3+x^4+x^5+x^6
$$

> There's no $$x^0$$ term because well a die doesn't have a $$0$$ and we're counting from $$1$$.

Similarly, if I had a $$2$$-sided die, the generating function would be $$x+x^2$$.

Now what if I rolled both the dice together and considered the sum of the numbers? Let's walk through this. The possibilities are really just a cartesian product:

$$
\{1, 2, 3, 4, 5, 6\} \times \{1, 2\} \equiv \{(1, 1), (2, 1), (3, 1), \dots, (6, 1), (1, 2), (2, 2), (3, 2), \dots, (6, 2)\}
$$

And to consider the sum, we just add the numbers in the ordered pair. So $$(6, 1)$$ corresponds to rolling a $$6$$ on the first die and rolling a $$1$$ on the second die. The sum is just adding those up.

Notice what happens if I multiply the two generating functions we had been working with:

- The exponents add up: $$x^6 \cdot x^1 = x^7$$. And their coefficients multiply.

- We can then simplify and get another polynomial by adding like terms.

The coefficients multiplying give us the total number of ways to obtain just that combination. Since it's just $$1$$s over here it might not be obvious, but say we had $$2x^6$$ and $$3x^1$$. Then **for each** $$6$$ we roll, there are $$3$$ ways for us to roll a $$1$$. Since there are $$2$$ ways for us to roll $$6$$, there are $$2\cdot 3 = 6$$ ways for us to roll a $$6$$ (first die) and a $$1$$ (second die). I think this should be obvious to most, but I couldn't find solace in omitting the explanation. 

Right so what matters is that we can just multiply the two generating functions to get a generating function for the set corresponding to their cartesian product!

> This product is actually called a convolution! It's a Cauchy Product when the participating series are infinite.

## Example 3

A final example before I go about listing some nice manipulations you could perform from the plethora of options. This is probably the most classic problem there is when someone needs to introduce generating functions:

Say we're so rich that we have an infinite collection of pennies, nickel and dimes. In how many ways can we shell out an exact change worth say $$k$$ cents?

> For those unfamiliar: A penny is worth $$1$$ cent, a nickel is worth $$5$$ cents and a dime is worth $$10$$ cents.

With each of the pennies, I can form a multiple of a cent with just that, so the generating function for it would be

$$
P(x) = 1+x+x^2+\dots = \frac{1}{1-x}
$$

> No pennies is trivial and still counts as an exact change.

Similarly, with the nickels I have the options of getting cents worth, $$5, 5\cdot 1, 5\cdot2, \dots$$ (each just one way). In other words, the generating function for nickels would be 

$$
N(x) = 1+(x^5)^1 + (x^5)^2 + \dots = \frac1{1-x^5} 
$$

You get the drill. The generating function for dimes would be 

$$
D(x) = \frac{1}{1-x^{10}}
$$

The answer's pretty simple. We just want the coefficient of $$x^k$$ in $$P(x)\cdot N(x)\cdot D(x)$$:

$$
\frac{1}{(1-x)(1-x^5)(1-x^{10})}
$$

Oookay maybe not so simple. How do we get a closed form for the $$k^\mathrm{th}$$ term? What is the power series representation? Well, you could use something like a Maclaurin series to get to it! In fact, use everything in your calculus repertoire to interpret this formal power series. You could find a lot of meaningful things! This is partly why we use these methods; we want to solve discrete stuff using calculus.

> Another method involves using the Extended Binomial Theorem for each of those functions and then calculating the $$k^\mathrm{th}$$ term of the resulting product. This post is becoming a bit long, so I will probably cover that in a separate short post! See [References](#references) for some resources for now.

> Oh and even if closed form expressions don't exist for some situation, generating functions are still quite convenient to deduce a lot of properties of a sequence.

## Manipulation Galore

*Deeeep breaths aaaaand here we GO!*

- Multiplying a generating function by $$x^{m}$$ "right-shifts" the resulting sequence by $$m$$ places and adds $$0$$ to those places: 

    $$
    x^3 \cdot (1+x+x^2) = x^3+x^4+x^5
    $$

    In here the first generating function we're multiplying $$x^3$$ by corresponds to the sequence $$1, 1, 1$$ while the resulting thingamajig corresponds to $$0, 0, 0, 1, 1, 1$$.

- Differentiating a generating function essentially does a "left-shift" and then multiplies each term of the sequence by its index:

    $$
    A(x) = a_0 + a_1x^1+a_2x^2+\dots \\
    A'(x) = a_1+2a_2x^1+3a_3x^2+\dots
    $$

- Notice how with those two rules in mind, the generating function for the sequence we abandoned before: $$1, 2, 3, \dots$$ (or $$a_n = n$$) is just 

    $$
    \frac{d}{dx} \left(\frac{1}{1-x}\right) = \frac{1}{(1-x)^2}
    $$

    Want to also tack on a zero? Well, just multiply by $$x$$!

- Say I have a generating function $$a_0+a_1x+a_2x^2$$ and I multiply it by $$\frac{1}{1-x}$$ aka $$1+x+x^2 +\dots.$$ What do we get? Well, I'll leave the calculations and reasoning to you (just try to multiply things out), but this is quite interesting!

    $$
    \frac{a_0+a_1x+a_2x^2}{1-x} \equiv a_0+(a_0+a_1)x+(a_0+a_1+a_2)x^2 + (a_0+a_1+a_2)x^3 +\dots
    $$

    The $$n^\mathrm{th}$$ term is now the sum of the first $$n$$ terms of the original sequence (of course if it's a finite sequence we get the same number of terms after a while)! I can't put into words how much this excited me when I first saw it. And I mean it makes sense: $$\frac{1}{1-x}$$ is a generating function itself. What does it correspond to? Well it just corresponds to a bunch of $$1$$s. The result we want is just a product of two generating functions, and that means the question for the $$n^\mathrm{th}$$ term of the product's sequence is "How many times do we get an $$x^n$$ when we multiply those two out?" The $$1$$s don't make a difference to the counts, and everything works out nicely.

# Concluding Notes

This is intended to be a small but complete introduction to the beautiful (and convenient!) world of generating functions. There are a lot of other things you could achieve. One example is solving recurrence equations! Perhaps I will make a post on it in the (not too distant) future! If you remember what I said at the very start of this post, I wanted to actually make a post on something else, but I just had to lay the groundwork with this post. So stay tuned for an exciting read when we apply generating functions to a very plausible question one might ask!

Until then, perhaps you might want to use your newfound tool-set to uncover a closed form expression for the Fibonacci numbers?

---

# References

Here are some more relevant documents, videos and suchlike on the Internet that one might find useful. These aren't necessarily things that I used to write this post, but they are definitely worth checking out to add to your understanding!

- [3b1b's video on Taylor Series](https://www.youtube.com/watch?v=3d6DsjIBzJ4)
- [Benjamin Hackl's blog post on generating functions](https://benjamin-hackl.at/blog/2022/06/generating-functions-3b1b.html)
- [AOPS Wiki on Generating Functions](https://artofproblemsolving.com/wiki/index.php/Generating_function)
- [MIT 6.042J Course Notes](https://www.math.cmu.edu/~ploh/docs/math/2011-228/mit-ocw-generating-func.pdf)
- [Herbert Wilf's Generatingfunctionology](https://www2.math.upenn.edu/~wilf/gfologyLinked2.pdf)
- [Analytic Combinatorics by Philippe Flajolet and Robert Sedgewick for the more advanced readers](https://algo.inria.fr/flajolet/Publications/book.pdf)
- [Cauchy Product on Wikipedia](https://en.wikipedia.org/wiki/Cauchy_product)
- [Chung-Chih Li, Kishan Mehrotra's notes on recurrence relations and generating functions](https://itk.ilstu.edu/faculty/chungli/DIS300/dis300chapter8.pdf)
- [ProofWiki Extended Binomial Theorem](https://proofwiki.org/wiki/Binomial_Theorem#Extended_Binomial_Theorem)
- [HMC Math's Notes on the Binomial Theorem](https://math.hmc.edu/calculus/hmc-mathematics-calculus-online-tutorials/precalculus/binomial-theorem/)