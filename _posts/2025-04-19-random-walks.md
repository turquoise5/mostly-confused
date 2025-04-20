---
title: "random walks"
date: 2025-04-19
mathjax: true
---

Here is an "elementary example of a random walk", according to the wikipedia page on random walks. 
You are on the number line $\mathbb{Z}$. Starting at 0, you randomly take a step to the right or to the left, i.e +1 or -1, with equal probability. 

Here is a question: where are you going to be after this game ends? Let's say it ends after 5 steps. 

Let $X_5$ is a random variable representing the number you will be at after 5 steps. $X_5$ could be any value between -5 to 5. To get to 5, you would have to take all steps forward. To get to 4 in five steps, one of your steps has to be a backwards step (to the left). To get to 3, there has to be 2 backwards steps, and so on. 

What if you want to get to 0? I don't thing there's a way to get to 0 after five steps; because five is an odd number, you can't cancel out every step you take. 

Alright then where are you expected to land?
$E[X] = \sum_{i=1}^5 i  P(\text{we land at i after 5 steps})$. For concision, rename $P(\text{we land at i after 5 steps})$ to $P_i$. 

For example, $P_5$ is the probability we land at 5 after five steps. Clearly, there's only one way to land at 5 after five steps; you would have to move forward five times. 

How about $P_4$? You would have to move forward four times and move backwards once (not necessarily in that order, it doesn't matter which step is the one you move back at). How many ways are there to move forwards 4 times and move backwards once? You can look at it as counting the number of steps the backwards step can be at. There are $5 \choose 1$ steps where we can move backwards; we can take the backwards step on the first step we take, or the 2nd one, or third, etc. 

This generalizes for positive i: $P_i = \frac{5 \choose i}{2^5} $, since there $2^5$ possible ways of playing this game.

What about negative numbers? In how many ways can you land at -5? Clearly one, again. And -4 has the same number of ways as 4 by similar logic. 

So, for -i: $P_{-i} = \frac{5 \choose -i}{2^5} $. 

But what about 0? For odd numbers, there's no way to get to 0. For even, there's only one way. If we can take 6 steps and want to get to 0, we must take 3 steps forward and 3 steps backwards, there's no other way.  

So $E[X_5] = \sum_{i=1}^5 i \cdot \frac{5 \choose i}{2^5} - \sum_{i=-5}^{-1} i \cdot \frac{5 \choose -i}{2^5} = \sum_{i=1}^5 i \cdot \frac{5 \choose i}{2^5} - \sum_{i=5}^1 -i \cdot \frac{5 \choose i}{2^5} = 2 \sum_{i=1}^5 i \cdot \frac{5 \choose i}{2^5} $. 

If we want to find the expectation after $n$ steps, $E[X_n] = 2 \sum_{i=1}^n i \cdot \frac{n \choose i}{2^n} = \frac{\sum_{i=1}^n i \cdot {n \choose i}}{2^{n-1}} $. We can ignore the case of 0 here since $P_i$ would be multiplied by 0, and would contribute nothing to the sum.

The numerator looks familiar?

After a cursory google search, I think I first encountered this when counting the number of ways you can pick i people out of n to create a club ($n \choose i$ ways), then out of the i people, you pick one to be the president ($p$ ways). There's another way to count the ways you can do that though, you can first choose the president of the club of of the n people (n ways to do that). There are two ays to place the rest of the $n - 1$ people, they can either be in the club or not. So the number of ways to form this club is $ 2^{n-1}$. This proves $i {n \choose i} = n 2^{n-1} $. There's a neat way to prove this algebraically as well: https://math.stackexchange.com/questions/7757/how-to-prove-this-binomial-identity-sum-r-0n-r-n-choose-r-n2n-1 

Finally: $E[X_n] = \frac{n2^{n-1}}{2^{n-1}} = n $ . So $E[X_5] = 5$. The answer is so simple, there must be an easier way to figure it out?
