# Robust_Parallel
A repo aimed at inducing a happy marriage between massively Parallelized RL training and robust sim2real deployment 

## Immediate TODOs: @Om @Mrigaank
- [x]: Have these two been merged before? i.e. has someone done parallelized training and then use a belief encoder model for RL? -> Mostly No.
- []: _Check if the performance boost would be significant?_ ->Immediate TODO can be done now that we have mujoco running?
- [x]: _Setup MUjoco Training on Summer - First Check if the implementation is correct and the robot will actually learn. -> Vel Tracking RL Training has been setup.
- []: _Setup Parallelized MUjoco Training on Summer - Integrate legged_gym with unitree_rl_mjlab. 
- [x]: _Check the deploy.yaml file created post training - with the mujoco setup, it isn't being created right now. -> Deploy.yaml file is being created with the unitree_rl_mjlab script.

## Sim2Real deployment: @Asavari,@Chirag
- [x]: We have the trained checkpoint from the Quadrupeds locomotion repo, can we deploy? --> Using unitree rl mjlab for training and deployment.
- []: A few things to keep in mind before deploying:
     a. Make sure there are proper constraints on the values the policy can output -> Clip the values action values to be within a range.
- [x]: _Compatibality check bw quadruped locomotion and unitree rl lab: check observation space and actor critic network structure._ --> irrelevant


## TODO:
Answer the following Questions first:
- [x]: What is it that the first work is lacking - https://arxiv.org/abs/2109.11978  -->@chirag 
    1. The Sim2Real deployment is not very robust. Also this method(their exact codebase) does not work for a GO2 for some reason.--> Lacks any type of sim to real deployment techniques (direct deploy).
    2. Instead of using legged_gym, can we switch to unitree_rl_gym or even better unitree_rl_lab? -> Repo[https://github.com/unitreerobotics/unitree_rl_lab] --> Unti tree RL gym is doable (ram and gpu constraints are met), RL Lab is not (requires 32GB ram and 16GB Vram). But unitree rl lab allows direct deployment to bot.
    3. If we do use unitree_rl_lab, what would be the VRAM and compute requirements for training. Or are there checkpoints available? --> No checkpoints available, not feasiable to use RL Lab for training.
- []: Is it possible to use the [quadrupeds_locomotion](https://github.com/Argo-Robot/quadrupeds_locomotion) checkpoint and deploy it in [untiree_rl_lab](https://github.com/unitreerobotics/unitree_rl_lab) --> @om and @chirag [05-02-2026] 
    1.[x] _Can we use unitree_rl_lab with mujoco. -> @Om [5-02-2026] --> Possible_
       - _Setup on Summer --> @Om_
    3. Directly deploy to IRL possible? -> @Om and @Chirag [07-02-2026] - (Not possible directly for Quadrupeds_locomotion)
    4. If there are issues such as network key mismatch:[post the above results] --> _This is transferrable since both the repositories are using the same learning library._
      - _Given that the checkpoints "look" transferrable, need to try the following: @Om_
       a. _Compare the checkpoint state dicts - should not be that different because rsl_rl._

- []: What component from the robust deployment paper needs to be incorporated - https://leggedrobotics.github.io/rl-perceptiveloco/  --> @asavari
     1. You will have to talk to Chirag here to see what is the contribution of the above paper(Parallelized Training). Basically the idea is that the first paper
        lacks sim2real deployment, the second one is good in that aspect - so the current implementation given, is that what we need? n
  
- []: This repo -> https://github.com/awesomericky/quadruped-robot-belief-encoder contains partial implementation of the above paper, analysis needed. @asavari
     1. Understand what components have been implemented from the paper - and are they enough? As in - in some aspect of the paper missing in the implementations.
     2. Add the implementation to the repo(not as a submodule because then we can't see what changes you make) - Add a separate Readme related to the repo explaining the above points.
     3. Is the current implementation of the paper runn-able? How does the setup look like? - Fork the existing implementation and try so that we can track the changes you make.
  
- []: Once the component has been found out, we need to think of an actual implementation of the idea in code and integration with first one @tbd

- [x]: Clone the legged_gym(Parallel Training) codebases as submodules.
    1. https://github.com/leggedrobotics/legged_gym.git  has been added
    2. #TODO - Can we use the one that depends on IsaacLab or Mujoco instead because IsaacGym is no longer supported? Will switching break things mentioned in the paper? @mrigaank -> done

