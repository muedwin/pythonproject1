# pythonproject1
# Project 1: Algorithmic trading (100 marks)

Algorithmic trading is the use of computer programs to automate stock trading decisions, based on available data such as share price or trading volume over different periods of time.

In this project, you will implement different trading strategies in Python, and put them to the test by evaluating their performance on simulated stock market data. This is a similar study as that done e.g. in [this paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0068344).

🚩 There is quite a lot of text to explain context -- to make sure you don't miss any tasks, they are marked with a little red flag (like in the tutorial sheets).

---

### Structure

You will **write a Python [package](https://docs.python.org/3/tutorial/modules.html#packages)** called `trading`. A package is basically a folder containing `.py` files (*modules*) with some function definitions inside -- you should see that this folder is already created in your repo. The package contain five [modules](https://docs.python.org/3/tutorial/modules.html#modules): `data.py`, `process.py`, `indicators.py`, `strategy.py`, and `performance.py`, as well as an initialisation script `__init__.py`.

You will write functions inside each module to perform different tasks. Then, you will use your custom modules in this Jupyter notebook to run your simulations. Just like for any other package, you will need to import it in the notebook first. For example, to use the function `create_portfolio()` in the `process.py` module, you can use

```python
import trading.process as proc
portfolio = proc.create_portfolio(...
```

The script `__init__.py` is just here to indicate that `trading` is a Python package, and not just a simple folder. It can remain empty.

Note that if, for example, your functions in your module `strategy.py` need any other modules to work (e.g. Numpy, pyplot, or one of your other custom modules...), you'll need to import them at the start of `strategy.py`. You'll also need to import them again if the code you use here (in the notebook) requires it.

Each task will give more detailed instructions of what should go in each module.

**Note:** if you change anything in one of your modules, even if you run the `import trading....` command again in the notebook, this **will not update** with the new version of your module. Instead, **restart the kernel** and import the module again to use your latest changes (Kernel > Restart in the toolbar).

---

### Working on your project with git and GitHub

- To **submit** your project, all you need to do is have your final version (ready for submission) **pushed to your GitHub repo**. At the deadline, we will clone all repos with `pp-project-1` in the name to collect your submissions.
- For that reason, **do not rename your repo** on GitHub! If you've renamed your repo and we cannot clone it at the deadline, you will be liable for **late penalties**.
- While working on the project, **commit your changes often** -- every time you make progress on a subtask. If you tend to forget to do this regularly, you could e.g. set a timer on your phone to remind you to commit every hour or so.
- You don't necessarily need to push your changes to GitHub every time you commit, although we'd strongly recommend that you **push them regularly**. This ensures that 1) you won't have any last-minute technical issues when it comes to submitting, and 2) you have an online backup of your work, just in case e.g. your computer breaks down.

---

### Academic integrity

This is an **individual** assignment -- just like for the Coderunner quizzes, the work your submit must be your own, to reflect and assess your own understanding and knowledge.

#### Collaboration vs. collusion

Collaboration is fine, but collusion is not. Concretely, this means that discussing the assignment **in broad terms** with others students is fine (and encouraged), as well as giving each other hints or general advice on how to approach a problem. You can use Piazza for this, for example -- if you are stuck, then please ask for help! However, you are **not permitted** to share your working (even partially) with other students -- that includes your code, any detailed description or explanation of code, and any results or analysis you perform.

For example:
- Alice and Bob are discussing the assignment on a Zoom call. Bob's code is not working for one of the questions, and he can't figure out why. He asks Alice how she's tackled the problem, and she explains her approach in broad terms. This gives Bob an idea, and he tries it later. *This is all fine.*
- Bob's idea doesn't work out, and he calls Alice again. He shares his screen with her to show his code. *This is getting dangerous* -- here's why:
    - Alice helps him with understanding the error, and gives him some pointers and ideas to try, without explaining the problem or the solution in much detail. *That would still be fine.*
    - Alice is stuck on the next question, though, and spots a couple of lines of Bob's code at the bottom of the screen. She uses some of that code for the next question in her submission. This is not OK: *both Bob and Alice have now committed misconduct* -- Alice by using Bob's code, and Bob by sharing his screen.
- Bob is still stuck. He posts his code for that question on Piazza. Some students help and also give him some  general advice. Charlie sees the post on Piazza, and didn't know how to start that question. Charlie uses some of Bob's code, with some corrections to fix the problems, and submits it for the assignment. *This is also misconduct* by both Bob and Charlie.
- Bob is still stuck (poor Bob!). It's getting very close to the deadline now, so he asks his friend Dara to *pleaaaase* show their solution, he promises not to copy it. Bob and Dara are really good friends, so Dara finds it difficult to refuse and sends their code. Bob rewrites Dara's code by changing some variable names, rearranging a bit, and paraphrasing the code comments so that they are "in his own words". *This is misconduct* by both Bob and Dara.

Use and trust your own judgement. It's important to understand that even with the best intentions, you expose yourself to academic misconduct as soon as you show your code to another student.

#### Providing references

Most of the code in your submission must be **authored by you**. That being said, you may use any code from the course material (e.g. workshop tasks, tutorial sheets, videos), without citing it.

You may also use **small pieces of code** (a few lines max at a time) that you found elsewhere -- e.g. examples from the documentation, a textbook, forums, blogs, etc... You may use this code *verbatim* (i.e. almost exactly as you found it), or adapt it to write your own solution.

A programming assignment is just like any other academic assignment -- and therefore, **you must provide a citation for any such code**, whether you use it *verbatim* or adapt it. To do so, include a code comment at the start of your script or notebook cell, indicating:
- the line numbers where the code was used or adapted,
- the URL of the source (or, if it's from a book, a full reference to the book),
- the date you accessed the source,
- the author of the code (if the information is available).

You can use this template -- delete one of the URL or book reference lines as appropriate:
```python
# Lines X-Y: Author Name
# URL: http://...
# Book Title, year published, page number.
# Accessed on 31 Nov 2020.
```

You must also provide **detailed code comments** for any such code, in your own words, to demonstrate that you fully understand how it works -- you will lose marks if you use external code without explaining it, even if it's cited correctly.

Remember to exercise caution if you use any code from external sources -- there are a lot of blogs and forums out there with very bad code! I'd recommend that you review the Week 4 video on searching the documentation.

With all that, we trust that you'll be able to use your best judgement, and to cite your sources appropriately -- if anything is not clear, please do ask. Note that **all submissions** will be automatically checked (and manually reviewed) for plagiarism and collusion, and [the University's academic misconduct policy](https://www.ed.ac.uk/academic-services/staff/discipline/academic-misconduct) applies.


---
## Task 1: Code review and debugging (30 marks)

Your junior colleague has started to work on the project. They started with writing the code to generate the simulated stock market data, for a number of stocks. Here is the brief for this part of the project:

> Generate simulated stock prices over a period of time, for a given number of companies, given share price at initial date, and volatility. Return data in a NumPy array, each column representing the price history for 1 company, and each row representing the share prices for all the stocks at a given date.
>
> The time increment is **1 day**, and share prices are given as the **closing price** each day.
>
> We assume that the [random walk hypothesis](https://en.wikipedia.org/wiki/Random_walk_hypothesis) holds. This means that the share price $p_t$ on a given day ($t>0$) and for a given company is normally given by
>
> $$
p_{t} = p_{t-1} + \Delta p_t,
$$
>
> where $\Delta p_t \sim N(0, \sigma^2)$ is the share price increment each day, normally distributed with mean $0$ and standard deviation $\sigma$. We take $\sigma$ to represent the inherent **volatility** of the stock.
>
> Whenever a share price dips to zero, we consider the company closed, and the daily share prices starting on that day until the end of the simulation should be set to `NaN`.
>
> We also model randomly occurring **important news** (e.g. political turmoil, a natural disaster, a new product announcement...), which have a positive or negative impact on share price over a number of days. This impact is modelled as a temporary **drift** $d$ in share price increments, positive or negative, with more or less magnitude depending on the volatility of the stock price.
> - Every day, there is a 1% chance of such an event happening, and immediately starting to impact the price of a given stock.
> - To represent that the news might impact an inherently more volatile stock more significantly than a less volatile stock, the drift $d$ is proportional to $\sigma$.
> - To represent that high-impact events happen more rarely, we choose $d = m \sigma$, with $m \sim N(0, 2^2)$ -- that is, the drift is equal to $m$ standard deviations of the usual increment. This means that the event is equally likely to be positive or negative, but that, for example, the magnitude of the drift is only about 5% likely to be greater than $4\sigma$.
> - When an event occurs, its impact lasts for anywhere between 3 days and 2 weeks -- i.e. the total duration is $t_{\text{event}} \sim U\{3, 14\}$.
> - The impact of several events occurring over the same time span is cumulative.
> 
> To summarise, the share price $p_t$ on a given day ($t>0$) and for a given company is given by
>
> $$
p_t = p_{t-1} + \Delta p_t + \sum_i d_i,
$$
>
> where each $d_i$ is the drift caused by an "active" event.
>
> For example: if the current day is $t = 15$, and
> - at $t = 10$, a negative event occurred, causing a drift $d_1$ lasting $6$ days,
> - at $t = 12$, another negative event occurred, causing a drift $d_2$ lasting $12$ days,
> - at $t = 15$ (today), a positive event occurs, causing a drift $d_3$ lasting $3$ days,
>
> then the share price today is given by
>
> $$ p_{15} = p_{14} + \Delta p_{15} + d_1 + d_2 + d_3. $$
>
> And tomorrow, if no event occurs, the first negative event will cease to have an impact:
>
> $$ p_{16} = p_{15} + \Delta p_{16} + d_2 + d_3. $$


Your colleague started working on the task, but they are now on parental leave, and they won't be back at work for a few months. You are tasked with continuing the project -- but first, as is good practice in the company, you should provide a **code review** for them, which they can read and learn from upon their return.

They didn't have time to properly test the code before leaving, and since you will continue working on the project, you also need to **test and debug** this code before going any further.

The definition of the function `generate_stock_price()` written by your colleague is in the `data.py` module, and here they call the function to generate the data. Your review should cover **all of the code** -- both the function definition and the use here.

import trading.data as data

# Make some data
N = 2
p0 = [200, 400]
v = [1, 2.5]
stock_prices = np.zeros([1000, N])
for i in range(N):
    stock_prices[:, i] = data.generate_stock_price(1000, p0[i], v[i])
plt.plot(stock_prices)
plt.show()

### 🚩 Your task

1. Write your **code review** in the Markdown cell below, as well as a report of any **bugs** you find in the code. Remember, as always, your feedback should be helpful and constructive, and help the author not only improve this code, but learn and improve their programming skills.

2. Then, revise the code: write a version which is free of bugs, and implement your review recommendations about structure and style. Any functions should be in `data.py`, and your code which calls the functions to generate data should be in the code cell below.

You can overwrite the buggy function in `data.py` with your new code -- you'll still be able to inspect the original code if you need, by looking at the first commit in the repo.

---
**💡 Tip**: when debugging code which uses random numbers, it's usually a good idea to test it on more consistent data. Depending on what you need to test:
- if you are testing features or parts of your code which don't rely on the data actually being random, then **remove the randomness!** Start with simple, predictable data, and build up the complexity.
    - **For example** (these are just suggestions, not instructions!), the function `news()` here has 3 random variables; can you first check that it gives the expected output if you assign fixed values to all 3? If it does, then does it still work if 1 of the variables is random but the other 2 are fixed? In `generate_stock_price()`, do you get the expected output if you set `inc` to a fixed number, and remove any adjustments to do with the news?
- if your test requires randomness, you can provide a **seed** to the generator (here, `np.random.default_rng()`) -- this ensures that running the code multiple times will always give the same numbers. [The documentation](https://numpy.org/doc/stable/reference/random/generator.html#numpy.random.default_rng) says that you can give a seed (an integer of your choice) as an input argument to `np.random.default_rng()`.
- another way to test with randomness is to run **lots of simulations** (with different seeds, this time).
    - For instance (still an illustrative example, not an instruction), in `news()`, you could check whether `m` is computed correctly by using the same command to generate many numbers, and plot a histogram of these numbers to check that it does look like the normal distribution with standard deviation 2.

And as always, when testing, start small and simple, and don't hesitate to `print()` and `plot()`!

---
**Note:** If your code is still not working, but you were not able to fix all the bugs, then you should provide any **tests** you run which show that the output is still not correct, and **explain where you think the error(s) come from**, to the best of your understanding. You should be able to achieve most of the marks for the task even if you don't fix every bug, as long as you can identify that there are still errors, provide test data which highlights them, and explain your insights and your reasoning as to where could the error be.

---

#### Bugs

*List any bugs you find in the code here. It may be convenient to refer to line numbers (View > Toggle Line Numbers if you can't see them).*

#### Code structure

*Write your comments and recommendations about the code structure here (object types used to handle data, use and structure of functions, loops, conditionals...).*

#### Code style

*Write your comments and recommendations about code style here (readability, style consistency, variable naming, code comments, docstrings...).*

#### Other recommendations

*Write any other recommendations or feedback for the author of the code, if you have any.*

---

# Write your revised and debugged version of the code here.



---
## Task 2: Trading strategies (70 marks)

You will now use simulation data to test different trading strategies. The goal is to:

1. Design a **trading strategy** -- an algorithm which will make buying or selling decisions based on certain rules, given the price data up to the current date.
2. **Deploy it** over 5 years of simulation data. We will need to write code to actually execute the buying and selling, and log the transactions.
3. Evaluate its **performance** over 5 years (in terms of profit made), and how it depends on different factors.

For all functions which have a precise specification, the **docstring** will already be written for each function you need to write, which will describe what the function needs to do, what input arguments it takes, and what output values it returns. When the assignment is released, all function definitions will only have the `pass` command -- which is just telling Python to do nothing. Remove the `pass` command and replace it with your code to define each function.

[As always, start by consulting the documentation if anything is unclear](https://docs.python.org/3/tutorial/controlflow.html#defining-functions).

The file `stock_data_5y.txt` contains data generated using the procedure from Task 1, for 20 different stocks over 5 years. The first row indicates the value used for volatility when the data was generated.

---

### 2.0. Retrieve data

🚩 In the `data.py` module, write a function `get_data()` to either generate simulation data (using the code from Task 1) or read pre-computed data from a file into a Numpy array `sim_data`. The user should be able to choose if they want to generate new data or read the data file.

---
**Note:** if you have not managed to completely debug the code in Task 1, you can do one of the following:
- Simplify the code from Task 1, by removing any impact from the news entirely.
- Only use the `method='read'` option when you call `get_data()`. You still need to fully implement the `method='generate'` option in `get_data()`, which will call the function `generate_stock_price()` -- you simply won't use that option in your simulations (because `generate_stock_price()` will still have bugs).

That way, you can still complete Task 2 and score up to the full 70 marks for it, even if you didn't complete Task 1.

---

### 2.1. Transaction processing

Let's start by writing functions which will actually do the work of buying and selling stock, updating our portfolio, and logging transactions in a ledger.

Write functions in the `process.py` module for this part.

#### Log transactions in a ledger

🚩 Every time we perform a transaction, we need to add a record of it to the ledger file. Write a function `log_transaction()` to log a transaction in a file `ledger.txt`.

#### Buying and selling

To keep track of how many shares we currently own for each stock, we will use a list `portfolio` of length `N` (where `N` is the number of different stocks available in the simulation), where each element is an integer indicating the number of shares we own for that stock.

For example, if there are 5 different stocks available, and we own 4 shares of stock `0` and 2 shares of stock `3`, then the list `portfolio` should be `[4, 0, 0, 2, 0]`.

Let's start with some simplifying assumptions:
- We will only hold a [*long position*](https://www.investopedia.com/ask/answers/100314/whats-difference-between-long-and-short-position-market.asp) -- this means that we will only be able to sell shares that we have already bought.
- Whenever we decide that it's a good time to sell shares for a given stock (based on our strategy), we'll sell *all* our shares at once.
- We have infinite money to spend (wouldn't that be nice? 😊)

🚩 Write a function `buy()` to purchase shares from a given company, using an allocated amount of money, and a function `sell()` to sell all the shares you own for a given stock. Both these functions should read and update the list `portfolio` **in-place** when you make a purchase or sell stock, as well as call `log_transaction()` to record the transaction in the ledger.

#### Create a portfolio

🚩 Write a function `create_portfolio()` which creates a portfolio with size `N`, calling the function `buy()` to purchase some shares on different stocks on the first day of the simulation.

The way we decide how many shares to buy of each stock on day 0 will be a part of our strategy later on.

#### Pause for testing

Before moving any further, it's time to do some testing to make sure all these parts are working together well.

🚩 In the code cell below, import your `data` and `process` modules.
- Use your function `get_data()` to read the 5 columns of `stock_data_5y.txt` with initial prices closest to 100, 120, 400, 250, and 300.
- Use your function `create_portfolio()` to create a test portfolio by buying shares for these 5 stocks, allocating 5000 to each stock, with fees of 20 per transaction.

You should obtain the following portfolio:
```
[49, 38, 12, 19, 15]
```
and you should see this data in `ledger.txt`:
```
buy,0,0,49,100.00,-4920.00
buy,0,1,38,130.00,-4960.00
buy,0,2,12,400.00,-4820.00
buy,0,3,19,260.00,-4960.00
buy,0,4,15,330.00,-4970.00
```

You should also check that this works when you generate data from scratch instead of reading it from the file.



### 2.2. Indicators

To implement a trading strategy, we will need to compute some **indicators** from the data over time, up to a given date. These indicators will help us make decisions about what to buy and sell, and when.

Remember that at any date you compute these indicators, you should only use **past** data.

Your functions for this part should go in the `indicators.py` module.

#### Moving averages

A moving average is simply an average (sometimes weighted) of the share price, calculated over a number of days. For example, the 7-day moving average at a given date is the average price over the 7 days leading up to the date. The moving average essentially smoothes out the high-frequency noise in the daily price data, allowing to see the more long-term variations.

🚩 Write a function `moving_average()` which calculates the $n$-day moving average for a stock over time. Your function should also be able to calculate weighted moving averages, if given a vector of weights.

#### Oscillators

An oscillator is a signal which generally indicates how well the price is doing today, relatively to how well it has been doing overall for the past $n$ days. Oscillators are a relative measure, given as a percentage. Two widely-used oscillators are the **stochastic oscillator** and the **relative strength index (RSI)**. When they reach certain thresholds, they can be used to make buying or selling decisions.

To calculate the level of the stochastic oscillator on a given day:

1. Find the highest and lowest prices over the past $n$ days.
2. Compute the difference between today's price and the lowest price, call it $\Delta$.
3. Compute the difference between the highest price and the lowest price, call it $\Delta_{\text{max}}$.
4. The level of the oscillator on this day is the ratio $\frac{\Delta}{\Delta_{\text{max}}}$.

To calculate the level of the RSI on a given day:

1. Calculate all the price differences on **consecutive days** over the past $n$ days.
2. Separate the positive differences (i.e. the price increased from one day to the next) from the negative differences (the price decreased from one day to the next).
3. Calculate the average of all the positive differences, and the absolute value of the average of all the negative differences.
4. Calculate the ratio between these 2 averages (positive/negative). Call this $RS$ (the relative strength).
5. The RSI on this day is given by $1 - \frac{1}{1+RS}$.

🚩 Write a function `oscillator()` which can calculate either the stochastic oscillator or the RSI over time (as indicated by the user), using a period of $n$ days.

---
### 2.3. Trading strategy

Now that we have all our tools ready to trade, it's time to deploy some trading strategies!

All your functions for this part should go in the `strategy.py` module. Note that since you will use functions from your `process.py` module, you should import it at the start of `strategy.py`. Since it's in the same folder, you don't need the `trading.` prefix there:
```python
import process as proc
```

There is a bit more freedom for you here in how you implement these functions, so we will only provide the docstring for `random()`, to give you an idea of what essential input data you'll need.

With every strategy:
- we start a new ledger file,
- we start with creating a portfolio on day 0 and invest some amount **equally** between all available stocks,
- we invest this same amount any time we buy shares,
- we finish with selling all remaining stock on the last day.

#### The "feeling lucky" strategy

The first "strategy" we'll try is the **random strategy**: we're going to decide randomly whether to buy or sell shares for each stock, and do this at regular time intervals.

🚩 Write a function `random()` which periodically, for each stock, decides whether to buy more shares, do nothing, or sell all your shares.

#### Crossing averages

This strategy involves computing 2 different moving averages over time, one "slow" and one "fast". Periods of 50 days and 200 days are often used, for instance. Since the fast moving average (FMA) will change more quickly than the slow moving average (SMA) when the share price changes, one could interpret the following:

- When the FMA crosses the SMA from below, then the share price is starting to rise significantly, and it's a good time to buy shares.
- When the FMA crosses the SMA from above, then the share price is starting to lower significantly, and it's a good time to sell shares before the price gets too low.

🚩 Write a function `crossing_averages()` which finds the crossing points between a SMA with period $n$ and a FMA with period $m$ to make buying or selling decisions.

#### Momentum trading using oscillators

Oscillators can help us guess if the price of a share is currently overvalued (*overbought*) or undervalued (*oversold*). Generally:
- the price is considered overvalued when the oscillator is above a threshold of 0.7 to 0.8 (good time to sell).
- the price is considered undervalued when the oscillator is below a threshold of 0.2 to 0.3 (good time to buy).

🚩 Write a function `momentum()` which uses a given oscillator (stochastic or RSI) with period $n$ to make buying or selling decisions, depending on a low threshold and a high threshold.

You should implement a minimum cool-down period after buying or selling, before making another transaction -- otherwise, if the oscillator crosses a threshold and stays beyond it for some time, you could end up buying shares every day for a while!

Alternatively, you could also wait until the oscillator has remained beyond a threshold for a few days before deciding to buy or sell.

#### Time for testing!

🚩 Test your functions in the code cell below, using data for one stock and a fairly short period of time (instead of 5 years). Run each of your functions on the data, plot relevant indicators, and check the ledger to see whether your strategies have performed the required transactions correctly.



---
### 2.4. Evaluation

Now that we've checked that our strategies worked, we can deploy them on lots of data and see how they do. Any functions you write for this part should go in `performance.py`.

#### Getting data from the ledger

The ledger created for each strategy will contain the key information as to how well it has performed.

🚩 Write a function `read_ledger()` which reads out data from a ledger file. Your function should report relevant overall information and display it on the screen in a readable manner, to get a quick glance at how much trading has been performed during the simulation by a given strategy. For example, you could report:
- the total number of transactions performed
- the total amount spent and earned over 5 years
- the overall profit or loss over 5 years
- the state of your portfolio just before the last day
- etc...

Your function should also produce a plot of the amount of money you had over time, starting from zero before buying the first shares. If you made a profit overall, then this graph should be above zero on the last day; if you made a loss, it will be below zero.

#### Run some simulations

🚩 In the code cell below (you can create more if you wish), run simulations using your different strategies.
- Use `get_data()` to read or simulate some data for 1 or more stock(s).
- Then, call 1 or more of your strategies to perform the simulation on the data.
- Finally, use `read_ledger()` to report results after each simulation.

Here are some of the ways you could evaluate your strategies -- you should try at least a couple of these. If you have other ideas for investigation, feel free to explore them too. You should plot and display any relevant data which helps the reader understand your findings.
- Produce a large, clearly labelled plot, showing the share price of one stock over time, the 2 moving averages used with `crossing_averages()` on the same graph, and the 2 different oscillators used with `momentum()` on a smaller graph below, with the time axes aligned. Find a way to indicate on the plots where the purchases and sales were made by each strategy.
- Find (or generate) data which seems to have a relatively strong upwards or downwards trend, and test your strategies on this data.
- Generate data for at least 20 stocks, all with the same initial price and volatility. This will allow you to more reliably evaluate the performance of a given strategy, by essentially repeating the experiment with the same parameters. How often does each strategy "win" (i.e. beat the other strategies in terms of final profit)? Can you find a measure of the reliability of each strategy?
- When operating on the same data, do the strategies (apart from `random()`) generally make purchases and sales at similar times? Can you explain why/why not?
- Experiment with different volatilities -- do certain strategies seem to perform better or worse for more volatile stocks?
- Experiment with different periods for the moving averages and the oscillators, and different decision thresholds or cool-down periods.

