# DRL-ice-hockey

The repository contains the codes about the network structure of paper "[Deep Reinforcement Learning in Ice Hockey
for Context-Aware Player Evaluation](https://arxiv.org/abs/1805.11088)".  

***Network Structure***:  

| name        | nodes           | activation function  |
| ------------- |:-------------:| -----:|
| LSTM Layer    | 512           | N/A |
| Fully Connected Layer 1| 1024     |  Relu |
| Fully Connected Layer 2| 1000      |  Relu |
| Fully Connected Layer 3| 3      |  N/A |

***Image of network structure***:  

<img src=./images/DP-lstm-model-structure.png alt="drawing" height="320" width="420"/>

<!---![model-structure](./images/DP-lstm-model-structure.png =250x250)--->

***Training method***  
We are using the on-policy prediction method [Sarsa](https://en.wikipedia.org/wiki/State%E2%80%93action%E2%80%93reward%E2%80%93state%E2%80%93action) (State–Action–Reward–State–Action).
It's a Temporal Difference learning method, and estimate the player performance by Q(s,a), where state s is a series of game contexts and action a is the motion of player.

***Running:***  
Use ```python td_three_prediction_lstm.py``` to run the neural network.  
Use ```python player_ranking_match_by_match_td_lstm.py``` to compute the player ranking metric.  
The origin works uses a private play-by-play dataset from [Sportlogiq](http://sportlogiq.com/en/).

If you want to run the network, please prepare your won sequential dataset, please organize the data according to network input in the format of Numpy. 
The neural network require three input: reward, state_input (conrtain both state features and one hot represetation of action) and state_trace_length, they must has the same length L (number of events in a game). We have trace length equals to 10, so reward is an L\*10 array, state_input is an L\*10\*feature_number array and state_trace_length is a one demensional vector tells the length of plays in a game.

***Package required:***  
1. Numpy 
2. Tensorflow
3. Scipy
4. Matplotlib

we are still updating this repository.
