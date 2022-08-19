# Initial Brainstorm
## Purpose of the model
This is the main thing to think about. Right now, our data is the values of one of the most popular technical indicators on TradingView. However, we have to decide what sort of inferrance we want to make from this data.

The most interesting approach would be for the model to make decisions to buy or sell the asset as it evaluates each new data-point. That would be the perfect representation of the algorithm. 

### Option 1 - Two Stage NN
We can use a two-stage NN approach to get to that level. 

We can create the first stage NN to give us a confidence level. The closer that value is to -1, the more confident the algorithm is about an incoming drop, the closer that value is to 1, the more confident for a sudden jump in share price. This (-1,1) output of course requires the output node to have TanH as the activation function.

Then, the second stage NN can take this confidence metric, and again, infer it as a sequential input. With the prediction of the model, the model can decide to BUY/SELL. The RNN would process the entire sequence, and for every point, based on the confidence, it would decide whether to HOLD/BUY/SELL. Based on the final sequence of these decisions, we can calculate profit and have that negated as the cost function.

### Option 2 - Genetic Algorithm with Decisions to Buy/Hold/Sell
Genetic algorithms are much simpler, and this might be just what it needs. If simulate the different agents, it is really easy to calculate their performance - the performance is just the profit that they make. 

An important point here is that if we ever use profit as the main "optimized value" then it requires that we make cost take into account the maximum profit that could have been made in the trade window we provide. 