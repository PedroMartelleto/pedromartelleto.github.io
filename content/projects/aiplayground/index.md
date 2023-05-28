---
title: "AI Playground"
icon: "https://img.icons8.com/external-flaticons-flat-flat-icons/64/000000/external-neural-network-the-future-flaticons-flat-flat-icons.png"
date: 2022-07-01
draft: false
project_tags: ["AI", "Web", "Typescript", "React"]
summary: "Visualizing neuroevolution in videogames"
weight: 1
---

<div>
<video src="https://github-production-user-asset-6210df.s3.amazonaws.com/35240934/128615672-2c77c06c-1d38-4093-a495-39a1024a2e58.mp4" autoplay="true" loop="true" />
</div>

### Demo and code
<p>
You can play around with app here: <a href="https://aiplayground.web.app">https://aiplayground.web.app</a>.

This project is open-source, and <a href="https://github.com/PedroMartelleto/AIPlayground">the code is available on Github</a>.
</p>

### About
<p>
This project is a web application that allows you to visualize the process of training a neural network to play a videogame ("environment"). The neural network is trained using a genetic algorithm called <a href="https://nn.cs.utexas.edu/downloads/papers/stanley.ec02.pdf">Neuroevolution of Augmenting Topologies</a>, which combines Darwinian evolution with artificial neural networks. Everything is coded from scratch in the browser using Typescript.
</p>

### How does it work?
<p>

The first thing we need is a fitness function that evaluates how well the agent is doing. For example, in the pole balancing environment, the fitness function is the amount of time that the pole is balanced. In the super mario environment, the fitness function is the amount of time that the agent is alive plus the progress that it makes in the level.

By using the fitness function, we can progressively select neural networks that perform better to propagate their genes to the next generation. To better explore the search space, we also introduce random mutations in the genes of the neural networks. This process is repeated for several generations until we get a neural network that performs well in the environment.

Here is a video of the agent playing super mario after training for a few hours:

<div>
  <video autoplay="true" controls="false" src="https://github.com/PedroMartelleto/CoviData/assets/35240934/7cb9f3ce-5557-4806-bb1c-cbd4bb961476"/>
</div>

</p>
