# ConvNetJS for Deep Learning at Hoberton School

Deep Learning - Introduction.
by Louis Monier and Gregory Renard.

## Introduction

The goals of this exercice are 
- to play with your first Neural Network based on the famous Javascript implementation of Neural networks by Andrej Karpathy : "ConvNetJS".
- to develop your intuition about Neural Network and observe how hyper-paramaters impact the learning curve.

ConvNetJS is a Javascript implementation of Neural networks, together with nice browser-based demos.
ConvNetJs is developed by Karpathy.  The original project : https://github.com/karpathy/convnetjs

## Requirements

- Download the GitHub repository : **Precise the URL of the GitHub**
- Open the web page in a browser : **ConvNetJS-HS-Demo.html**

## Task 1 : Observation

After opened the page, you can observe 3 parts :
- the setup of a neural network (#1 = top)
- the graphic representation of the distribution of points (#2 = bottom left)
- the transformed representation of all grid points in given layer. (#3 = bottom right)

![alt tag](https://github.com/gregrenard/hs/blob/master/ConvNetJS/images/capture1.png)

```javascript

// species a 2-layers neural network with one hidden layer of 1 neurons
layer_defs = [];

//input layer declares size of input. here: 2-D data
// ConvNetJS works on 3-Dimensional volumes (sx, sy, depth), but if you're not dealing with images
// then the first two dimensions (sx, sy) will always be kept at size 1
layer_defs.push({type:'input', out_sx:1, out_sy:1, out_depth:2});

// declare 1 neurons, followed by tanh ()
layer_defs.push({type:'fc', num_neurons:1, activation: 'tanh'});

layer_defs.push({type:'softmax', num_classes:2});

net = new convnetjs.Net();
net.makeLayers(layer_defs);

trainer = new convnetjs.SGDTrainer(net, {learning_rate:0.01, momentum:0.1, batch_size:10, l2_decay:0.001});

```


## Task 2 : Adaptation

