# Momentum_Oscillator_Trading
Experimenting with trading strategies utilizing an oscillator approach (Low Latency)

This is a preliminary analysis so far. However, a working Oscillator is displayed. Accuracy score for model: 0.8559404172830689

Oscillations can be thought of as sigmoid functions i.e. this is a classifica- tion So we take this minute by minute dataset, and create features based on this HH-LL designation.
In this analysis I chose to use a LSTM (Long-Short Term Memory) net- work to try to build the Oscillator. LSTMs are usually the go-to for time-series based Deep Learning algorithms. LSTMs are a type of recurrent neural net- work (RNN) architecture that can capture both forward-looking and backward- looking dependencies in sequential data.
Really the goal is to implement a sigmoid function in the last predictive layer of a sequential Neural Network.
So, I’ve created arbitrary HH,HL,LH,LL designations based on the 1-minute pricing data for various time designations: 1, 2, 5, 15, 60 minutes. An example of the data set is clearly displayed in the jupyter notebook.


These serve as the primary features for the model.
Additionally, since this is a time-series problem, I deconstructed the time- stamp into features: on what month, at what time, etc.
Finally, as far as the data set up goes, using a Simple Moving Average strat- egy, I calculated exit and entry points as I needed to find a total return target variable. The target thus becomes when Total Return after an entry and exit is positive.

As there were very few positive tar- get values (when Total Return was positive), I needed to re-balance the weights (Class Weights).
The rest of this set up is quite traditional for LSTM classifiers: sigmoid function in the last layer, an ADAM optimizer, loss being calculated by binary cross-entropy.
Model was trained for 10 epochs.
The display of the oscillator was made using a Moving Average with a win- dow size of 10 days.
Results are presented in the confusion matrix.

# Next steps

Experiment with various different DL models for better model performance and trend analysis. One curious way to go may be via converting the time-series into graph signals and utilizing Graphical Neural Networks (GNN).

-Find best/worst case returns for intraday signals
-Produce a single output oscillator based on training '
-Forecast at the horizon what has been trained with both lookback / look- ahead as is needed for both 
1) knowing that a price action pivot point occurred and
2) that an entry signal had a path to a good or bad outcome.
3) actual price action pivot point

