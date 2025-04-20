---
title: "random walks"
date: 2025-04-19
---

Here is an 'elementary example of a random walk', according to the wikipedia page on random walks. 
You are on the number line $\mathbb{Z}$, and starting at 0, you randomly take a step to the right or to the left, i.e +1 or -1, with equal probability. 
Here is a question: where are you going to be after, say, 5 steps? 
Let $X_5$ is a random variable representing the number you will be at after 5 steps. $X_5$ could be anywhere from -5 to 5. To get to 5, you would have to talk all steps forward. To get to 4 in five steps, one of your steps has to be a backwards step. To get to 3, there has to be 2 backwards steps, and so on. Hmm, what if you want to get to 0? I don't thing there's a way to get to 0 after five steps; because five is an odd number, you can't cancel out every step you take. 

Alright then where are you expected to land?
$E[X] = \sum_{i=1}^5 i P(we land at i after 5 steps)$. For concision, rename $P(we land at i after 5 steps)$ to $P_i$. 

For example, $P_5$ is the probability we land at 5 after five steps. Clearly, there's only one way to land at 5 after five steps; you would have to move forward five times. 
How about $P_4$? You would have to move forward four times and move backwards once (not necessarily in that order, it doesn't matter which step is the one you move back at). How many ways are there to move forwards 4 times and move backwards once? You can view it as counting the number of steps the backwards step can be at. There are $5 \choose 1$ steps where we can move backwards; we can take the backwards step on the first steps we take, or the 2nd one, or third, etc. 
This generalizes: $P_i = {5 \choose i} $. 

So $E[X_5] = \sum_{i=0}^5 i \frac{n \choose i}{2^5} $. Of course, if we want to find the expectation after $n$ steps, $E[X_n] = \sum_{i=0}^n i \frac{n \choose i}{2^n} $.This looks like something I've seen before?

After a cursory google search, I think I first encountered this when counting the number of ways you can pick pick i people out of n to create a club ($n \choose i$ ways), then out of the i people, you pick one to be the president ($p$ ways). There's another way to count the ways you can do that though, you can first choose the president of the club of of the n people (n ways to do that). There are two ays to place the rest of the $n - 1$ people, they can either be in the club or not. So the number of ways to form this club is $ 2^{n-1}$. This proves $i {n \choose i} = n 2^{n-1} $. There's a neat way to prove this algebracally as well: https://math.stackexchange.com/questions/7757/how-to-prove-this-binomial-identity-sum-r-0n-r-n-choose-r-n2n-1 

Finally: $E[X_n] = \frac{n 2^{n - 1}}{2^n} = \frac{n}{2}$ . So $E[X_5] = 2.5$. The answer is so simple, there must be an easier to way to figure it out?

