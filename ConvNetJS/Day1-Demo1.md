# Deep Learning Introduction with ConvNetJS at Hoberton School

Deep Learning Day 1 by Louis Monier and Gregory Renard.
https://www.holbertonschool.com/

## Requirements

- Download the GitHub repository : **Precise the URL of the GitHub**
- Open the web page in a browser : **ConvNetJS-HS-Demo.html**

We recommend you use Chrome as your browser.

## Task 1 : Observation

![Start](/images/capture1.png)
![Start](https://github.com/gregrenard/hs/blob/master/ConvNetJS/images/capture1.png)

As you open the page, the Network start to train itself.
You can observe 3 parts :

1. the setup of a neural network (#1 = top)
2. the graphic representation of the distribution of points (#2 = bottom left)
3. the transformed representation of all grid points in given layer. (#3 = bottom right)
 
The 1st part (Setup of the Neural Network) present the structure of the current Network.  Every Network is a linear list of layers.
The 1st layer is must be the 'input' (where you declare sizes of your input), the last layer must be a loss layer ('softmax' or 'svm' for classification, or 'regression' for regression)



Below the description of the code at the initial load of the page :


```javascript

// species a 1-layers neural network with one hidden layer of 1 neurons
layer_defs = [];

//input layer declares size of input. here: 2-D data
// ConvNetJS works on 3-Dimensional volumes (sx, sy, depth), but if you're not dealing with images
// then the first two dimensions (sx, sy) will always be kept at size 1
layer_defs.push({type:'input', out_sx:1, out_sy:1, out_depth:2});

// declare 1 neurons, followed by a tanh
layer_defs.push({type:'fc', num_neurons:1, activation: 'tanh'});

// declare the linear classifier on top of the previous hidden layer
layer_defs.push({type:'softmax', num_classes:2});

// Network instantiation and layers definition
net = new convnetjs.Net();
net.makeLayers(layer_defs);

// species the trainer as a SGD+Momentum trainer.  Performs a weight update every 10 examples (batch size)
trainer = new convnetjs.SGDTrainer(net, {learning_rate:0.01, momentum:0.1, batch_size:10, l2_decay:0.001});

```

Notice the network separates in 2 regions through a line only.
If you edit the Network, don't forget to click on the button : "change network".

## Task 2 : Add a point

As you're seeing the training of the Network, you can click at any place of the graph to add a new red or green point.
- CLICK: Add red data point
- SHIFT+CLICK: Add green data point
- CTRL+CLICK: Remove closest data point

You can observe the classification's evolution. 

## Task 3 : Change the distribution shape 

After you add points in the distribution, you can change the distribution shape by clicking on the buttons : simple, circle, spiral, ring, check, spots or target.

![More Neurons](/images/capture2.png)
![More Neurons](https://github.com/gregrenard/hs/blob/master/ConvNetJS/images/capture2.png)

You can observe the difficulty of your current Network to identify the right classification model.  

**Solve it :** Increase the number of neurons "num_neurons:1" to 2, 3, 5... in the layer type 'fc' and try again the different shapes.

*Don't forget to click on the button **"Change network"** to apply your modification !*

```javascript
// species a 1-layers neural network with one hidden layer of 5 neurons
layer_defs = [];
layer_defs.push({type:'input', out_sx:1, out_sy:1, out_depth:2});

// declare 5 neurons, followed by a tanh
layer_defs.push({type:'fc', num_neurons:5, activation: 'tanh'});

layer_defs.push({type:'softmax', num_classes:2});

```

You can observe the training of the Network seems producing a better model for some type of shapes as the 'Check'.

![alt tag](/images/capture3.png)
![alt tag](https://github.com/gregrenard/hs/blob/master/ConvNetJS/images/capture3.png)


Exercices :
- Write down how many neurons it takes for the network to master each shape in less than a minute.
- How many neurons does it take to get the "target" to converge quickly?

How can we optimise our Network ?

## Task 4 : Add layers to your Network

Now you can try to add a layer to your Network with the replication of the whole line with type 'fc' and change the number of neurons to 10.

```javascript
// species a 2-layers neural network with one hidden layer of 10 neurons
layer_defs = [];
layer_defs.push({type:'input', out_sx:1, out_sy:1, out_depth:2});

// declare 10 neurons, followed by a tanh
layer_defs.push({type:'fc', num_neurons:10, activation: 'tanh'});
layer_defs.push({type:'fc', num_neurons:10, activation: 'tanh'});

layer_defs.push({type:'softmax', num_classes:2});

```

After replicated the whole line with "num_neurons:". Now you have a 2-layer network.

![Add Layers](/images/capture4.png)
![Add Layers](https://github.com/gregrenard/hs/blob/master/ConvNetJS/images/capture4.png)

**How quickly can it crack the "target"?**