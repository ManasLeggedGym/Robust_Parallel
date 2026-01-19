# Robust_Parallel
A repo aimed at inducing a happy marriage between massively Parallelized RL training and robust sim2real deployment 

## TODO:
Answer the following Questions first:
- []: What is it that the first work is lacking - https://arxiv.org/abs/2109.11978 
    1. The Sim2Real deployment is not very robust. Also this method(their exact codebase) does not work for a GO2 for some reason.
 
- []: What component from the robust deplyment paper needs to be incorporated - https://leggedrobotics.github.io/rl-perceptiveloco/
- []: Once the component has been found out, we need to think of an actual implementation of the idea in code and integration with first one 
- [x]: Clone the legged_gym(Parallel Training) codebases as submodules.
    1. https://github.com/leggedrobotics/legged_gym.git  has been added #TODO - Can we use the one that depeds on IsaacLab or Mujoco instead because IsaacGym is no longer supported? Will switching break things mentioned in the paper?


