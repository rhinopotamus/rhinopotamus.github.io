---
layout: post
title: Yesterday was a good day
categories:
- sbagleyteaches
---


It's Friday afternoon, I'm pretty much caught up with grading, nothing is pressing, so it seems like a good time for a moderately self-indulgent blog post. I had a really good day in the classroom yesterday -- no, you know what, scratch that, I felt like I kicked ass -- and I think it might be useful for me to recap what happened and reflect on why I felt so good about stuff.




#### The context




I'm currently teaching a summer semester DATA 220. This is our version of your usual intro-level service stats course that's required by whatever departments across the university. Ours is taught using [a nice set of R modules](https://github.com/VectorPosse/Intro_Stats) designed for RStudio to handle computations, which frees us up to talk more in class about using your human brain for the process of meaningful inference. Our summer semester is 8 weeks long as opposed to the usual 15 or 16, which means that the course is highly compressed, even though we meet in three-hour blocks rather than the usual two-hour blocks. I've got 12 students enrolled in the course, approximately 10 of which are going to show up on any given day. I also have a colleague sitting in on the course just to learn some statistics. Students sit at hexagon tables in groups of two or three, and there's three big whiteboards at the back of the room that I mostly use as student space.




#### The plan




The topic for yesterday's class was t-tests of two means -- both paired means and independent means. My plan was to focus on how to decide whether data are paired or independent, then look at an example that would allow us to discuss checking conditions and interpreting a confidence interval. This is pretty representative of the kinds of things I like to spend time on: human brain stuff that **you** need to think about **before** interacting with a computer.




#### Part 1: A student question




At the beginning of class I asked if people had any questions from previous classes. The main question that emerged was in relation to a recent assignment I gave them about interpreting confidence intervals. In particular I asked them, when we say "we're 95% confident that the true population whatever is between blah and blah", what do we really mean? Percentages are always **of** something, so 95% **of what**? This is a hard question, even for like actual scientists (see [1](http://www.ejwagenmakers.com/inpress/HoekstraEtAlPBR.pdf) [2](https://link.springer.com/article/10.1007/s10654-016-0149-3)), and the right answer is quite technical\*, so students always struggle with this. One of the R modules I linked above contains a pretty nice discussion of the issue -- in particular, it gives examples of three or four common misinterpretations of the confidence interval -- so I told students to be sure to read that when they were composing their answers. 




So, a student asked about this part of the assignment, and this question launched us into a long, profitable discussion about confidence intervals. I decided to bring in another one of the problems on the assignment, which I'll just screencap here:




![](https://sbagleyteaches.wordpress.com/wp-content/uploads/2019/07/image-1.png)Exercise 3.6 from [Introductory Statistics with Randomization and Simulation](https://www.openintro.org/stat/textbook.php?stat_book=isrs)


 We read through the discussion in the R module together, and then I asked students to illustrate the misinterpretations in the R module by seeing which of the statements in Exercise 3.6 was similar. (The statements labeled (a) and (c) are incorrect for reasons discussed in the module.) This went really well, and it showed students how useful the discussion at the end of the R module actually was -- by necessity, it's quite a technical discussion, and I think a lot of people read it with their eyes glazed over before we dove into it together in class.




I then called back to another exercise on this assignment: "A survey found that 52% of U.S. Twitter users get at least some of their news from Twitter, with a confidence interval from 45.8% to 58.2%. Does this survey give statistically significant evidence that **more than half** of U.S. Twitter users get some news from Twitter?" This is an example of a very common way that people will lie with statistics, either intentionally or unintentionally: they'll report a point estimate without acknowledging a margin of error. I asked students to do a [one-minute paper](http://oncourseworkshop.com/self-awareness/one-minute-paper/) (one of my favorite little active learning techniques!) writing a better sentence reporting the result of this survey: still understandable to a layperson, but more statistically responsible. We then combined ideas to make a good sentence that the whole class agreed on. I don't remember exactly what we came up with, but something like, "Probably somewhere between 45% and 58% of U.S. Twitter users get some of their news from Twitter." I do remember that they insisted on the "probably."




This whole discussion was so great. I really enjoy the affordance that the three-hour block gives me to dig deep into things I didn't necessarily plan to do. We got to talk about the extremely relevant issue of people lying with statistics, I got to insist on precision in language, we saw the relevance of class resources, we built connections between various problems on an assignment, and we left with everybody feeling more solid in their understanding of confidence intervals. (Also, I felt pretty secure in my own content understanding; this has not been a given in previous statistics classes since I'd never actually taken one before I started teaching them. :) )




#### Part 2: Paired vs. not-paired activity




So next we moved into the planned portion of class. Before class, I'd given the students some reading from the book about paired vs. independent samples. However, I follow our textbook in hating the term "independent samples" because of the immediate conflation with "independent" as in "not associated," so I called them "paired" and "not-paired" data. In the [reading quiz](https://cft.vanderbilt.edu/guides-sub-pages/just-in-time-teaching-jitt/) (on Canvas and due one hour before class), I asked students to take a stab at defining paired vs. not-paired data, and give examples of both. 




The first thing we did in this segment of class was another one-minute paper where I had them recall in a sentence or two their answers to the reading quiz, and then [compare their sentences with the other people sitting at their table](https://teachingcommons.stanford.edu/resources/learning/learning-activities/think-pair-share). After they'd had some time to discuss, we talked as a whole class about this, and got some words out, including "correspondence" and "groups," that would be useful later. I told them that my point with this activity was that it's hard to give a definition in words, and I wanted to introduce another tool, which is to look at the shape of the dataframe:




![](https://sbagleyteaches.wordpress.com/wp-content/uploads/2019/07/image-2.png)Paired and not-paired data frames. Tables from [ISRS](https://openintro.org/stat/textbook.php?stat_book=isrs).


Looking at the dataframe, it's much easier to see the difference: in paired data, each case has values of two numerical variables; in not-paired data, each case just has one numerical variable (that we're interested in), but the cases fall into two groups.




I then rehashed an activity I'd used in a previous semester: I asked each group to pick their favorite examples of paired and not-paired data someone came up with on the reading quiz, draw a dataframe for their example on one of the back boards, and use their drawing to explain why the data are paired vs. not-paired. This was a fun activity. People got super into it. There was a lot of argument within each group about what the variables should be called and what each case was (which was exactly my point: in order to decide whether the data is paired or not paired, you need to think hard about what a case is, and what the variables are). Eventually, each of the three groups had a couple of dataframes drawn up.




At this point, I suddenly thought about an activity I'd done in a different course: a mini poster session. Kinda making this up on the fly, I told students that someone from each group **besides** the person who had the marker while drawing the dataframes had to stay and be the presenter, and then the other members of the group would go and visit the other groups. Not to toot my own horn *too* much here, but honk honk, this was **awesome**. I was really happy with how this activity forced everyone in the group to be accountable for the group's work. As soon as I described what was happening, I saw a couple of students who had previously been less-involved get nominated to be the presenters, and then start asking their groupmates really seriously about how to explain their examples.




After the poster session, I had them look at an exercise that's going to be on this week's homework:




![](https://sbagleyteaches.wordpress.com/wp-content/uploads/2019/07/image-3.png)Exercise 4.14 from [ISRS](https://www.openintro.org/stat/textbook.php?stat_book=isrs)


I assigned each group to one of these three scenarios. The group chat went pretty quick, but the class discussion afterwards was really interesting: group (a) talked about how, depending on how you interpret the sentence, their scenario could be either paired or not-paired. This made me so happy to see that my students were comfortable with ambiguity and weren't pushing for "but what's the riiight answer???".




#### Part 3: Sheep heart attacks example




The next thing on our docket was an example: data from an experiment testing the use of an embryonic stem cell treatment on 18 sheep that had a heart attack. (I didn't previously know that sheep could have heart attacks, but I guess they have hearts, so sure, why not.) We had a quick discussion about whether the data would be paired or not-paired, and then moved into checking conditions for using the t-test.




One of the conditions as we've set them up is to ensure that the sample is less than 10% of the population. (This is part of checking independence of observations.) At this point a student said, "I'm not sure about this one, because, what's the population? Is it just sheep in this farm, or what?"




I love this question because it is absolutely a human brain question. This is absolutely the kind of question I want my students asking. This question opened a door for us to have a really good discussion about the relationship between sample and population: what do you, with your human brain, think is a reasonable broader population for your particular sample to generalize to? We threw out a bunch of ideas (sheep in this barn, sheep on this farm, sheep in this city, sheep in this state, sheep in the US, sheep in the entire world, whatever particular breed of sheep, etc. etc.), and then I had them rate how comfortable they felt generalizing our sample of 18 sheep to these various different populations. I concluded this bit by saying, my point is that there is **no right answer** to this question (to which a student said, "Well, why didn't you just say that at the beginning?!") -- there is only a **right thought process**. 




We wrapped up this example by looking at a confidence interval (that I got from RStudio and am not particularly interested in the computational details, thanks) and using it to answer our important real-world question: did the treatment work?




So much great stuff happened in this segment. A student felt comfortable asking a great question that spurred us into an important discussion about a human brain part of statistics. We were able to tie back to previous understandings of confidence intervals. Students made good real-world conclusions and backed them up with meaningful statistical evidence.




#### Part 4: Work time




We finished up with some time for students to work on their term group projects. I wandered around and helped answer questions that came up. This was also super fun. Everybody was very engaged in their own little world of personally-interesting data. Even when class time was officially up, and I packed up to go home, two students were **still** working together on an interesting thing they'd found. Nothing warms my grubby little soul more than students getting really interested in something and ignoring the time. :)




#### Some umbrella thoughts




Beyond all the individual blow-by-blow reasons, I had some sort of overarching thoughts while reflecting on why I felt like this class went so well. Really, they boil down to that I felt **capable**. Because I now have a good toolbox of active learning techniques that I've developed over the last few years, I was able to deploy interesting activities at useful times. I remixed some old stuff and threw in some new stuff and improvised like crazy. Also, because this is now the third time I've taught DATA 220, I feel pretty solid in my content knowledge, even for tricky technical points. I feel like I have a reasonable handle (that will only get better) on what things students will find confusing, and on what the high-leverage ideas are for breaking confusion. What's more, I now have a depth of experience that allows me to identify **that** a class went super well, and the reflective tools to think critically about **why**.




Ultimately, I'm writing this blog post to a future myself, because I know there's going to be a future day where I feel way less capable than I did about this class session, and this will be a good reminder for me:




Some days, I really love my job. :)




\* Were we to take a whole bunch of random samples, and correctly construct a 95% confidence interval from each one, then we could expect approximately 95% **of those confidence intervals** to capture the true population parameter. (See, that's tricky.) 



