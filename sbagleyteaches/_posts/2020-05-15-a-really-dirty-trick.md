---
layout: post
title: A really dirty trick
categories:
- sbagleyteaches
---


It's probably been said, and if not then I'm saying it right here, that differential equations is the systematic study of dirty tricks. Here's a good one I encountered in the 1924 monograph on the calculus of variations that I'm rendering into an [online PreTeXt book](https://rhinopotamus.github.io/cov/var-book.html).




For various reasons, we're looking at the differential equation




$ \displaystyle (y-\alpha)(1+(y')^2) = 2b$, 




where $ b$ is a constant. This equation is separable, but if you separate, you get




$ \displaystyle \sqrt{\frac{y-\alpha}{2b-(y-\alpha)}} dy = dx$,




which I don't see a great way to integrate. This means it's probably 




### Time for a dirty trick




The thing that was annoying to me in that integral is the square root, which came about because I decided to isolate $ y'$. So I wonder what would happen if I solved for $ y$ instead:




$ \displaystyle y-\alpha = \frac{2b}{1+(y')^2}$




Well now we're getting somewhere. If I'm in a calculus headspace and I see anything that remotely resembles $ 1 + x^2$ in a denominator, I immediately want to make the trigonometric substitution $ x = \tan \theta$. So, what the hell, let's just say $ y' = \tan \theta$ and see what happens.




$ \displaystyle y-\alpha = \frac{2b}{1+(y')^2} = \frac{2b}{1+(\tan \theta)^2} = 2b \cos^2\theta$ 




I'm liking this outcome for a couple of reasons:




* The derivative has gone away!!
* No more annoying fraction!!
* I've got a pretty reasonable thing for $ y$!! It's in terms of $ \theta$ instead of $ x$, but worse things have happened.
* And actually, that gives me another good idea: maybe I'll temporarily abandon my goal of writing down an explicit function $ y(x)$ in favor of writing down parametric equations $ (x(\theta), y(\theta))$ for my solution curve.




In service of that new goal, where is $ x$, anyway? The only place $ x$ is occurring is hidden away in $ y'$, which really means $ \frac{dy}{dx}$. Since I made that substitution $ y' = \tan \theta$, that really means $ \frac{dy}{dx} = \tan \theta$. By the inverse function theorem, this is the same as $ \frac{dx}{dy} = \frac{1}{\tan\theta}$. That's nice, but I really need to know $ \frac{dx}{d\theta}$ if I'm gonna recover a function $ x(\theta)$.




But hey, I already know $ \frac{dx}{dy}$, and I also know $ y(\theta)$, so I could easily figure out $ \frac{dy}{d\theta}$ -- it's just $ 4b\cos\theta(-\sin\theta)$. So now I can abuse the chain rule:




$ \displaystyle \frac{dx}{d\theta} = \frac{dx}{dy}\frac{dy}{d\theta} = \frac{1}{\tan\theta} (-4b\cos\theta\sin\theta) = -4b \cos^2\theta.$




That's easy enough to integrate using the power-reducing identity.




### Getting a little dirtier




Do you know, that thing I just got for $ \frac{dx}{d\theta}$ looks a lot like the thing I got for $ y-\alpha$ -- I'm just off by a factor of -2. I wonder if I pick, for my original dirty trick, $ y'=-\tan\left(\frac{\theta}{2}\right)$ instead of just $ \tan\theta$?




$ \displaystyle y-\alpha=\frac{2b}{1+\tan^2\left(\frac{\theta}{2}\right)} = 2b \cos^2\frac{\theta}{2}$




$ \displaystyle \frac{dy}{d\theta} = 4b \cos\frac{\theta}{2} \cdot -\sin\frac{\theta}{2}\cdot \frac{1}{2} = -2b \cos\frac{\theta}{2} \sin\frac{\theta}{2}$




$ \displaystyle \frac{dx}{d\theta} = \frac{dx}{dy}\frac{dy}{d\theta} = -\frac{1}{\tan\frac{\theta}{2}} \left( -2b \cos\frac{\theta}{2} \sin\frac{\theta}{2} \right) = 2b \cos^2\frac{\theta}{2}$




Nice, so now that we made our trick just a little dirtier, we've now got something that looks really symmetric, and integrating $ \frac{dx}{d\theta}$ is at least no more difficult than it was before.



