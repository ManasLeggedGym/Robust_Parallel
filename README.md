# Robust_Parallel
A repo aimed at inducing a happy marriage between massively Parallelized RL training and robust sim2real deployment 

## TODO:
Answer the following Questions first:
- []: What is it that the first work is lacking - https://arxiv.org/abs/2109.11978  -->@chirag
    1. The Sim2Real deployment is not very robust. Also this method(their exact codebase) does not work for a GO2 for some reason. --> "We do not apply any additional filtering or constraint satisfaction checks." As stated this paper dosent employ any kind of sendor fusion or correction. For better sim to real deployment we can look into other methods where they use GRUs (Belief encoder) to fuse  proprioceptive and exteroceptive data. They also mention starting to train the student netwoek with no noise and gradually increase noise.
           - https://ieeexplore.ieee.org/document/8392399: updating the map using EKFs, issues: registers overhands as tall objects.
    2. Instead of using legged_gym, can we switch to unitree_rl_gym or even better unitree_rl_lab? -> Repo[https://github.com/unitreerobotics/unitree_rl_lab]
    3. If we do use unitree_rl_lab, what would be the VRAM and compute requirements for training. Or are there checkpoints available?

     
- []: What component from the robust deployment paper needs to be incorporated - https://leggedrobotics.github.io/rl-perceptiveloco/  --> @asavari
     a. You will have to talk to Chirag here to see what is the contribution of the above paper(Parallelized Training). Basically the idea is that the first paper
        lacks sim2real deployment, the second one is good in that aspect - so the current implementation given, is that what we need? n
  
- []: This repo -> https://github.com/awesomericky/quadruped-robot-belief-encoder contains partial implementation of the above paper, analysis needed. @asavari
     a. Understand what components have been implemented from the paper - and are they enough? As in - in some aspect of the paper missing in the implementations.
     b. Add the implementation to the repo(not as a submodule because then we can't see what changes you make) - Add a separate Readme related to the repo explaining the above points.
     c. Is the current implementation of the paper runn-able? How does the setup look like? - Fork the existing implementation and try so that we can track the changes you make.
  
- []: Once the component has been found out, we need to think of an actual implementation of the idea in code and integration with first one @tbd

- [x]: Clone the legged_gym(Parallel Training) codebases as submodules.
    1. https://github.com/leggedrobotics/legged_gym.git  has been added
    2. #TODO - Can we use the one that depends on IsaacLab or Mujoco instead because IsaacGym is no longer supported? Will switching break things mentioned in the paper? @mrigaank

