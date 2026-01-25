# Robust_Parallel
A repo aimed at inducing a happy marriage between massively Parallelized RL training and robust sim2real deployment 

## TODO:
Answer the following Questions first:
- []: What is it that the first work is lacking - https://arxiv.org/abs/2109.11978  -->@chirag
    1. The Sim2Real deployment is not very robust. Also this method(their exact codebase) does not work for a GO2 for some reason.
    2. Instead of using legged_gym, can we switch to unitree_rl_gym or even better unitree_rl_lab? -> Repo[https://github.com/unitreerobotics/unitree_rl_lab]
    3. If we do use unitree_rl_lab, what would be the VRAM and compute requirements for training. Or are there checkpoints available?

     
- []: What component from the robust deployment paper needs to be incorporated - https://leggedrobotics.github.io/rl-perceptiveloco/  --> @asavari
- []: This repo -> https://github.com/awesomericky/quadruped-robot-belief-encoder contains partial implementation of the above paper, analysis needed. @asavari 
- []: Once the component has been found out, we need to think of an actual implementation of the idea in code and integration with first one @tbd

- [x]: Clone the legged_gym(Parallel Training) codebases as submodules.
    1. https://github.com/leggedrobotics/legged_gym.git  has been added #TODO - Can we use the one that depends on IsaacLab or Mujoco instead because IsaacGym is no longer supported? Will switching break things mentioned in the paper?

