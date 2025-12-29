---
layout: post
title: Midpoint vs trapezoid estimates
categories:
- sbagleyteaches
---


Today I have been playing around trying to justify an observation that we made in my Calculus II class, which is as follows:




*Observation 1.* On a region where $ f$ has consistent concavity, the error from the trapezoid sum is about twice the error of the midpoint sum, and has the opposite sign. (In fancy symbols: $ E\_\text{trap} \approx -2\cdot E\_\text{mid}$.)




It's fairly easy to arrive at this observation by just doing a bunch of calculations. A fun activity for a Calculus II class is to reproduce [Table 5.6.5](https://activecalculus.org/single/sec-5-6-num-int.html#ixQ) from Active Calculus; if you divide-and-conquer across a couple different groups, you can do this pretty easily in 15 minutes with appropriate use of technology. Then you just look at the column of errors, and say, gee whiz, Observation 1.




But then a student asked me why this is true. This was surprisingly tricky to run down. I scribbled about it for like three pages, most of which just ended up being, like, "let's do some calculus now; by talos that was just geometry!!" I think I now have a reasonably convincing justification that I can at least handwave to the student in question, without too much additional technology. (Note that we are at the beginning of Calculus II, so in particular I don't want to say the words "Taylor series" yet.)




Setup
-----




*Observation 2*. To be more precise, the trapezoids in the trapezoid rule are trapezoids whose tops are secant lines to $ f$.




*Observation 3.* Midpoint rectangles are actually trapezoids whose tops are tangent to $ f$ at the midpoint.




*Proof by picture.* This is [Figure 5.6.3](https://activecalculus.org/single/sec-5-6-num-int.html#jDj) from Active Calculus. For the sake of argument, I'm going to follow this figure throughout; notice that we can assume without loss of generality that the function is concave up. Say that the edges of the rectangles / trapezoids occur at $ x=a$ and $ x=b$.




![](https://activecalculus.org/single/external/images/5_6_MidVTrap.svg)


If you want a little more symbolic convincing, write down the equation for this tangent line: $ L(x) = f\left(\frac{a+b}{2}\right) + f'\left(\frac{a+b}{2}\right)\left(x-\frac{a+b}{2}\right)$. Compute $ \int\_a^b L(x)\ dx$ and observe that you get the area of the midpoint rectangle.




(Aside: Observation 3 would actually be true no matter what slope you picked for this diagonal line. It's just convenient to pick the slope of the tangent line.)




*Observation 4.* The secant lines in question are damn near parallel to the tangent lines in question.




*Justification.* The slope of this secant line is $ \dfrac{f(b)-f(a)}{b-a}$. This is in fact the [central difference approximation](https://activecalculus.org/single/sec-1-5-units.html#Opr) to the slope of the tangent line, $ f'\left(\frac{a+b}{2}\right)$.




*Observation 5.* Therefore, the secant line is pretty much just a vertical shift of the tangent line: if $ S(x)$ is the secant line and $ L(x)$ is the tangent line, then $ S(x) \approx L(x) + \varepsilon$ for some small constant $ \varepsilon$. Specifically, $ \varepsilon = f(a) - L(a)$ would be a good choice; that's the specific amount we'd need to scoot up by to get the left endpoints to match.




### Idea of the proof




With this setup stuff established, I can now say the following, which will give you some idea of what we're up to with the symbol-pushy stuff below. The idea is that since there's such a nice relationship between the trapezoid-rule trapezoid and the midpoint-rule trapezoid (they only differ by a little parallelogram!), we probably have a nice relationship between their errors. Meditate upon the following picture ([Figure 5.6.4](https://activecalculus.org/single/sec-5-6-num-int.html#PKs)) before proceeding. I'll just point out that the height of the parallelogram is $ \varepsilon$ and the width is $ (b-a)$.




![](https://activecalculus.org/single/external/images/5_6_MidTrapError.svg)


Nitty-gritty details
--------------------




I'm noticing that we haven't used our "consistent concavity" hypothesis yet. By "consistent concavity" we probably mean that $ f''(x)$ is approximately constant on the big interval of which our little rectangle $ [a, b]$ is a subinterval. 




*Observation 6.* If $ f$ has "consistent concavity," then it's approximately quadratic.




*Proof.* Suppose $ f''(x) \approx Q$ for some constant $ Q$. Integrate twice and don't forget your arbitrary constants:




$ f'(x) = \int f''(x)\ dx \approx \int Q\ dx = Qx + C$




$ f(x) = \int f'(x) \ dx \approx \int Qx + C \ dx = \frac{Q}{2} x^2 + Cx + D$




Okay, but which quadratic? We may as well ask for the linear part of $ f(x)$ to match the tangent line $ L(x)$:




$ f(x) \approx \underbrace{\left[f\left(\tfrac{a+b}{2}\right) + f'\left(\tfrac{a+b}{2}\right)\left(x-\tfrac{a+b}{2}\right)\right]}\_{L(x)} + B \cdot \left(x-\tfrac{a+b}{2}\right)^2$




Soon we will learn the word "Taylor series" and this will seem more natural. For now, think of it as, we're taking the linear approximation $ L(x)$ and sticking on some bendiness with a quadratic term $ B \cdot \left(x-\tfrac{a+b}{2}\right)^2$. (The B stands for "bendiness.")




*Observation 7.* On this little subinterval, the error from the midpoint rule is $ E\_\text{mid} = \int\_a^b L(x) - f(x)\ dx = \int\_a^b -B\cdot \left(x-\tfrac{a+b}{2}\right)^2\ dx = \left[-\frac{B}{3} \left(x-\tfrac{a+b}{2}\right)^3 \right|\_a^b$.




(Note: that's the $ \frac{\cdot}{3}$ that I'm going to talk about at the very end of this post.)




Algebra time: this is $ -\frac{B}{3}\left(\left(\frac{b-a}{2}\right)^3 - \left(\frac{a-b}{2}\right)^3\right) = -\frac{B}{3}\cdot 2\left(\frac{b-a}{2}\right)^3 = -\frac{B}{12}(b-a)^3$.




Notice, btw, that when the function is concave up, B is positive, so this value works out to be negative, which makes sense, because the midpoint rule should underestimate the true value.




*Observation 8.* The error from the trapezoid rule is $ E\_\text{trap} = \int\_a^b S(x) - f(x)\ dx.$ Using Observation 5, this is $ \int\_a^b \varepsilon + L(x) - f(x)\ dx = \int\_a^b \varepsilon \ dx + \int\_a^b L(x) - f(x)\ dx$. Integrating a constant is easy, and the second integral is the one we just did in Observation 7. So we can conclude that $ E\_\text{trap} = \varepsilon\cdot(b-a) + E\_\text{mid}$.




(Looking back at the "idea of the proof" picture, $ \varepsilon \cdot (b-a)$ is the area of the parallelogram you have to stack on top of the midpoint-rule trapezoid to get the trapezoid-rule trapezoid. So this makes sense: if you take the whole parallelogram and subtract the pink parts $ E\_\text{mid}$, you ought to get the red part $ E\_\text{trap}$. Why does it say + above instead of -, you ask? Good question: because $ E\_\text{mid}$ is *negative*.)




Guess what: we're back to where we started!




The prestige
------------




*Observation 1, re-stated*: $ E\_\text{trap} \approx -2 E\_\text{mid}$.




*Proof.* Let's monkey around with this claim a bit. Since (by Observation 8) $ E\_\text{trap} = \varepsilon\cdot(b-a) + E\_\text{mid}$, this claim is equivalent to claiming that $ \varepsilon\cdot(b-a) + E\_\text{mid} \approx -2 E\_\text{mid}$, or that $ \varepsilon\cdot(b-a) \approx -3 E\_\text{mid}$. Then by Observation 7, $ E\_\text{mid} \approx -\frac{B}{12}(b-a)^3$, so the claim is that $ \varepsilon\cdot(b-a) \approx -3\cdot \left(-\frac{B}{12}(b-a)^3\right) = \frac{B}{4}(b-a)^3$. I'm going to divide out a $ (b-a)$ on both sides, and pull a 2 inside a parentheses, to arrive at:




*Claim that's equivalent to Observation 1:* $ \varepsilon \approx B\left(\frac{b-a}{2}\right)^2$.




Why is this true, then? Well, what was $ \varepsilon$ anyway? That came from Observation 5, where we said that $ \varepsilon = f(a) - L(a)$ was the amount by which we'd need to shift $ L(x)$ up to get it to match $ S(x)$, and we also said that it's the amount by which the linear approximation undershoots the actual function.




What's neat, though, is that we now know a little more about $ f(x)$ than we did before. Specifically, Observation 6 told us that $ f(x) = L(x) + B \cdot \left(x-\tfrac{a+b}{2}\right)^2$. 




Therefore, $ f(x) - L(x) = B \cdot \left(x-\tfrac{a+b}{2}\right)^2$. Plug in $ a$: the LHS is $ \varepsilon$ and the RHS is exactly what we thought it should be.




The moral of the story
----------------------




Let's return to [Figure 5.6.4](https://activecalculus.org/single/sec-5-6-num-int.html#PKs) and we can tell a more interesting story now:




![](https://activecalculus.org/single/external/images/5_6_MidTrapError.svg)


* Zooming in on the tangent line and the blue curve $ f$: This last claim is basically saying that the amount by which the tangent line undershoots the function is controlled by (1) the bendiness of the function and (2) the width of the (sub)interval we're looking at.

* Notice also that the only reason this problem is interesting is that the blue line is *curved*. If it just went straight from the left corner to the middle and then straight from the middle to the right corner, then it'd cut the parallelogram into two equal pieces. Instead, *because it bends down*, there's more red than pink.

* Because the blue line is basically *quadratic*, it turns out that there's basically half as much pink as there is red. If the function was allowed to *wiggle* as well as bend, then that ratio may not turn out to be so nice.

* Specifically, the blue line cuts the trapezoid in such a way that the pink is 1/3 of the total. Where does that 3 come from? It comes *precisely* from integrating $ (\text{---})^2$.



