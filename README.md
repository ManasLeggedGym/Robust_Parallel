# Quadruped Robot Belief Encoder
Implementation of some core elements of "Learning robust perceptive locomotion for quadrupedal robots in the wild" [[Paper](https://www.science.org/doi/10.1126/scirobotics.abk2822)]

<img width=1000 src='image/figure.png'>

## Description
This repository includes implementation of two elements.
1. Student policy network
2. Heightmap noise generator

Student policy network is composed of **belief encoder** and **belief decoder** to appropriately fuse both proprioceptive and exteroceptive sensor data. It is implemented in *Python*. 
Privilege information decoder, included in the paper, is excluded because they were not that critical in our experiement.

Heightmap noise generator is composed of **three noise models** to handle errors available in real-world use cases due to depth camera noise, state estimation error/drift etc. 
It is implemented in *C++* because the [Raisim](https://raisim.com/) simulator that we are actively using implements environments in *C++* for fast simulation.

## Dependencies
- numpy
- pytorch
- ruamel.yaml

## Run example
1. Student policy network
```
cd model
python main.py
```

2. Heightmap noise generator
```
cd noise_generator
mkdir build && cd build
cmake ..
make
# After build is finished
./noise_example
```
## Components from [Wild ANYmal](https://leggedrobotics.github.io/rl-perceptiveloco/assets/pdf/wild_anymal.pdf) that need to be incorporated
- *Belief Encoder Network*: A recurrent neural network (GRU /RNN) that encodes proprioceptive and exteroceptive observations into a latent belief state i.e. the terrain representation. This belief state allows the policy to reason over partial, noisy and temporally accumulated perception data which as a result improves robustness to sensor noise and occlusions.
  
- *Teacher-Student Imitation*: The teacher policy is trained via Reinforcement Learning ( RL) with full access to privileged information in the form of the ground-truth state of the environment. This privileged training enables the teacher policy to discover the optimal behavior given perfect knowledge of the terrain. Then, a student policy is trained that only has access to information that is available in the field on the physical robot. The student policy is built around the belief state encoder and trained via imitation learning. The student policy learns to predict the teacher’s optimal action given only partial and noisy observations of the environment.
  
- *Height Sample and Domain Randomization*:
  - During student training, random noise is injected into the height samples using a parameterized noise model. Each noise value is sampled from a Gaussian distribution. Additionally, three mapping conditions are defined with associated noise parameters *'z'* to simulate changing map quality and error sources.
  - For domain randomization, the masses of the robot’s body and legs, the initial joint position and velocity, and the initial body orientation and velocity are randomized in each episode. In addition, external force and torque are applied to the body of the robot and the friction coefficients of the feet are occasionally set to a low value to introduce slippage.

## Contributor
- [Yunho Kim](https://github.com/awesomericky)
- [Jinhyeok Choi](https://github.com/Triangle2022)
