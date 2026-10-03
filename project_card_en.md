# Project Card: Alpha221 – Intelligent investment portfolio optimizer with a strict risk limit

**Team 4**
* Kacper Nowaczyk (31838)
* Adam Remfeld (31799)
* Nikodem Boniecki (31865)

## 1. For whom and why? 
The system helps retail investors build a diversified stock portfolio (focusing on AI, gamedev, and semiconductor sectors). It solves the problem of complex mathematical balancing of profit and risk by automatically providing optimized weights for selected stocks to maximize the potential expected return while maintaining a strict risk limit (an unexceedable level of variance/volatility) set by the user.

## 2. Which technology from the laboratory scope?
The problem belongs to the optimization class. The solution will be based on a custom implementation of a genetic algorithm.

## 3. Where does the data come from?
We will use an official, fully legal API providing selected market data:
* **Dataset name:** Tiingo End-of-Day (EOD) Stock API
* **Size:** Data downloaded dynamically in JSON format. We assume analyzing a basket of approx. 50-100 stocks over a 5-year horizon (the data payload for a single query is a few megabytes).
* **License:** Tiingo API Free Tier / Internal Use Only (official, free developer license intended for academic and personal use).
* **Link:** https://api.tiingo.com/

## 4. What do you implement yourselves?
We independently implement the entire artificial intelligence core: a genetic algorithm from scratch. This includes custom mechanisms for selection, crossover, mutation, and a fitness function that promotes higher investment returns while applying a severe penalty for exceeding the established risk limit. Standard libraries (such as `requests`, `pandas`, and `numpy`) will be used exclusively for communicating with the Tiingo API, preprocessing input data (calculating daily returns), and initially calculating the covariance matrix.

## 8. Success criterion / Baseline
The effectiveness of our genetic algorithm (achieved return given the risk limit, and computational performance) will be evaluated on the same test dataset and compared against two baselines:
1. **Markowitz Model (Mean-Variance Optimization)** – as the exact, analytical expert solution.
2. **Naive Portfolio (1/N)** – representing a basic strategy of equal capital distribution (without targeted risk optimization).