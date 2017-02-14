# Multi-Armed Bandit

* Example would be you go to a casino and you have a choice between 3 slot machines
* (for now) each machine gives a reward of 0 or 1 
* this is calle the multi-Armed Bandit problrm because you have to pull on the arm of a machine and they are bandaits because they are trying to take your money
* the win rate is unknow ex.it could be: 0.1, 0.3, 0.5 but you wouldnt know its your job to discover it by collecting dat 
* now your goal at the casino is to maximize your winnings
* if your psychic and you knew the winning rates you would only playthe machine with the best winning rate
* now since you dont know the wining rates you need to estimate them by collecting data, that means you have to play each of the machines
* this is where the dilemma come in you need to collect alot of dta for your estimates to be accerate, but if you collect lots of data your going to spend lots of money playig sub optimal bandits
* so the key is balancing between maximizing your earings and trying to obtain accurate messuraments of each bandits win rate, because to max your earnings you need to know this information

# Explore Exploit Dilemma

## first Solution - Epsolon-Greedy Stragety
* simple, used throughout this course
* we use a small number called Epsilon as probbability of exploration
* typical vales of Epsilon is 5%, 10%
* below is sudo code
```
p = ramdom()
if p < epsolon:
    pull random arm
else:
    pull current-best arm
```
* to explain the above basically at each round we generate a random number is the random number is less than epsolon we explore (choose an arm at random), if the random number is greater than epsilon we exploit meaning we choose the arm that has the best maximum so far so it should be clear from here you will eventually learn which arm will be the best, even if our initial guess is wrong because every arm has the opportunity to be updated.
* Eventually, we'll discover which arm is the true best, since this allows us to update every arm's estimate
* Epsilon-Greedy in the long run, allows us to explore each arm an infinite numer of times
* Promblem: we get to a point where we explore when we dont need to
* epsolpon = 10%, we'll contiue to spend 10% of the time doing suboptimal things
*  a/b test could useful here where at some predetermined time if there is statistical significance, then set epsilon=0 if there is evidance or proof to do so

### Estimating Bandit Rewards
* if we assume that are rewards are not just coin tosses, so we dont need to just store a number of successes and failurs
* the general method of solving this problem is to use the mean
* this works for coin tosses too 
* ex p(k=1)=(#of1's)/(#of1's + #of0's) = (#of1's)/N
* this issue is how do you calculate the smaeple mean of a random varible
* we know its the total sum divided by the number of samples
![totalSumDividedNumberOfSamples](/../master/lesson1/totalSumDividedNumberOfSamples.png?raw=true "total sum divided number of samples")
* issue with the above equationis is that all x's would need to be stored to calculate the mean and thats not efficient
* it would be better to calculated from old mean
![totalSumCalculatedFromOldMean](/../master/lesson1/calculateFromOldMean.png?raw=true "total sum divided number of samples")

## second solution - Optimistic Initial values method
* suppose we knew the mean of each bandit wasmuch less than 10
* pick a high ceiling as the initial mean estimate
![Optimistic Initial Values mean](/../master/lesson1/beforeNowOptimistic.png?raw=true "optimistic initial values new mean")
* the initial sample meani is "oo good to be true"
* all collected data will cause it to go down
* if the true meanis 1, the sample mean will still approach1 as Icollect more samples
* all means will eventually settle into their true values(exploitation)

## third solution - UCB1
* main idea behind UCB1 is confidence bounds
* intuitively, we know that a sample mean from 10 samples is less accurate than a sample mean from 1000 samples
* Chernoff-Hoeffding bound:
![Chernoff-Hoeffding bound](/../master/lesson1/chernoff-HoeffdingBound.png?raw=true "chernoff-Hoeffding bound")
* looks complicated, but leads to a simpler algo
![simpler algo](/../master/lesson1/simplerAlgo.png?raw=true " simpler algo")
* N = number of times ive played in total, N^j = numer of times ive played bandit j
