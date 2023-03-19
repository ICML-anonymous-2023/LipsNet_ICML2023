# ICML 2023 Rebuttal: LipsNet

## For reviewer \#oVCx
All of the reward curves are shown below.

There is not obvious reduce of sample efficiency.

- LQR
<img src="./materials/TAR_s2a1.png" width = "40%" height = "40%"/>

- Vehicle Trajectory Tracking
<img src="./materials/TAR_veh2dof.png" width = "40%" height = "40%"/>

- DMControl Cartpole
<img src="./materials/TAR_cartpole.png" width = "40%" height = "40%"/>

- DMControl Reacher
<img src="./materials/TAR_reacher.png" width = "40%" height = "40%"/>

- DMControl Cheetah
<img src="./materials/TAR_cheetah.png" width = "40%" height = "40%"/>

- DMControl Walker
<img src="./materials/TAR_walker.png" width = "40%" height = "40%"/>

<br />

As for the Cartpole environment, it only needs few steps to reach stability.

The maximum steps in DMControl are 1000. But Cartpole only needs about 200 steps to become stable, as the following videos show.

- Cartpole: TD3 (MLP)



<br />

- Cartpole: TD3 (LipsNet-G)



<br />

- Cartpole: TD3 (LipsNet-L)



<br />

When the global Lipschitz continuity holds, all states have the same Lipschitz constant. The Cartpole exhibits rapid changes in action when it points down, and small changes in action when it is stable in upright upward. To ensure good performance, LipsNet-G learns a large global Lipschitz constant to capture the rapid changing action. However, Cartpole only needs few steps to reach stability (the max steps are 1000 in dmc, but cartpole only needs about 200 steps to be stable). For LipsNet-G, the remaining 800 steps after stabilization is also under large Lipschitz constant, which leads to large action fluctuation. As a result, LipsNet-G's overall fluctuation ratio exceeds those of MLP. This is precisely why we proposed LipsNet-L, which can learn different local Lipschitz constants for different states.

<br />

In the following videos, we add observation noise.

The noise is uniformly distributed between [-0.2, -0.2, -0.2, -0.3, -0.3] and [ 0.2,  0.2,  0.2,  0.3,  0.3].

- Cartpole: TD3 (MLP)



<br />

- Cartpole: TD3 (LipsNet-G)



<br />

- Cartpole: TD3 (LipsNet-L)



<br />