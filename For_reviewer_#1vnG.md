# ICML 2023 Rebuttal: LipsNet

## For reviewer \#1vnG
To demonstrate why LipsNet is highly effective at attenuating action fluctuation in some environments (e.g., LQR, vehicle trajectory tracking, CartPole, Reacher), we visualize the Reacher environment with observation noise.

In Reacher environment, we need to apply force and make the pole's endpoint keep inside the target red sphere.
The position of target sphere is randomly initialized.


- Reacher: TD3 (MLP)

https://user-images.githubusercontent.com/33803151/226159136-2412f7cf-867f-4cf1-b3e8-95bb1129756d.mov

<br />

- Reacher: TD3 (LipsNet-L)

https://user-images.githubusercontent.com/33803151/226159138-f294e249-1899-4a8d-b6e5-a892354a4818.mov

<br />

The above vidoes show that:
1. The maximum steps in Reacher is 1000, but only a few steps are need to rotate the endpoint inside the target sphere.
2. After the endpoint inside target sphere, the MLP poliy produce fluctuating action due to observation noise.
2. After the endpoint inside target sphere, the LipsNet poliy produce stable action.

Therefore, LipsNet can keep almost unchanged action after the first few steps. However, MLP has fluctuating action in all the 1000 steps. This is the exact reason why LipsNet is highly effective in this kind of environments.
