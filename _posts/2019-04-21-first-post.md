---
title: Basics of Artificial Intelligence
author: Lawrence XIAO Delong
layout: post
---
I am really grateful that I have the chance to take both 'Intro to AI' and 'Machine Learning' modules this semester. There were really challenges but I have my thoughts after completion of both team projects.

Intro to AI:
The team project requires us to build a poker bot to play against each others' bots in heads-up limited Texas Hold'Em. 
1. Algorithm: The state-of-the-art poker agents like Alberta's have already solved this game so far using Counterfactual Regret Minimization. My team evaluated different approaches and realised that this is indeed better than Minimax and Deep Q-Learning because it allows the use of bucketing to effectively reduce game tree size at no cost of optimal game strategy. Also, it gives agent the ability to learn bluffing. By the way, try to refrain from using imperfect recall in CFR, because it does not lead to Nash-equilibrium.
2. Hand Strength Evaluation: We learnt that card relative is not the only thing that matter but also card potential. For example, a 2-Spade and a 3-Spade is a set of low cards in early poker game (preflop street), but it has high potential for late game due to suiteness and closeness. We found out that Chen's formula encapsulates this idea. It both provides a near-normal distribution and is more efficient than monte-carlo simulation. For late game (flop, turn, river streets), a look-up table of monte-carlo simulation results is preferred.
3. Training: Yes, this is the most challenging part! Throughout that stage, we wished to have a supercomputer. Although NUS has a computer cluster with GPU powers, it is spammed by many other students. We resorted back to our own computer resources which are slow, therefore need enhancement. One method is to make use of all logical threads instead of merely one. We used a python API called 'joblib' with dast.distributed as backend scheduler for the recursive computation of CFR values down the game tree during training.

Machine Learning:
The team project gives freedom of topic selection. My group opted for image classfication problem on hydroponic roots.
1. Algorithm: Undeniably, Convolutional Neural Network is the best and there are a lot of pre-trained models from the annual ImageNet Large Scale Visual Recognition Challenge. You can simply take a world-leading model and add your own customised top layer to suit your classification needs. This would give you incredible results.
2. Image Format: However, our image format of GrayScale 256x256 pixels does not fit into the required RGB 299x299 pixels of Xception model. That is still fine, with a channel of 3 (RGB), a GrayScale image can still be well interpreted using pre-trained RGB neural nets.
3. Training: Another problem will be the lack of RAM on our laptop to do such a large-scale training of 299x299x3 images. Thus, what is proposed is to manipulate the batch size to a larger value, which can still produce very good results without consuming much of our RAM.