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

## first Solution
* Epsolon-Greedy Stragety
* simple, used throughout this course
* we use a small number called Epsilon as probbability of exploration





