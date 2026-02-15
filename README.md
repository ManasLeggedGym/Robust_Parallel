# Robust_Parallel
A repo aimed at inducing a happy marriage between massively Parallelized RL training and robust sim2real deployment 

## Immediate TODOs: @Om @Mrigaank
- []: _Check if the performance boost would be significant?_ ->Immediate TODO can be done now that we have mujoco running?
- []: _Setup Parallelized MUjoco Training on Summer - Integrate legged_gym with unitree_rl_mjlab. -> Deadline: [16-02-2026]

## Implementation of perceptiveloco: @Asavari @Chirag
- []: Modify unitree_rl_mjlab training script with the actor-critic architecture and belief encoder.
     - [] Imp - Whatever we are training/implementing - have bash scripts for them to make reproduciblity easier.
     - [] a. Implement teacher policy from https://github.com/awesomericky/quadruped-robot-belief-encoder --@Asavari and @Chirag - Decuple check :[17-02-2026]
     - [] b. Incorporate student network, height sampling, and domain randomization @Asavari - Check(DECUPLE) [17-02-2026]
     - [] Create a fork of unitree_mjlab and link the origin with the setup on summer. [17-02-2026]
     - [] c. Edit the observation space with respect to https://leggedrobotics.github.io/rl-perceptiveloco/ --@Chirag - partially done
     - [] d. Check the training scripts that are already present - do we need to code something additional?
     - [] e. What does the training setup look like? - IRL and SIM?

- []: RQ - Once the component has been found out, we need to think of an actual implementation of the idea in code and integration with first one @tbd


