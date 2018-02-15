# CarND-Controls-PID
## Self-Driving Car Engineer Nanodegree Program

---

To tune the hyper parameters for MPC, I started by focusing on the Kp. I started by making this value 1, but found that the car swerved much more aggressively than was ideal. I continued to decrease this by 50% each time until the swerving was less aggressive, but still aggressive enough to make its way around curves. I settled on a value of .25. At this point, it seemed the car would not stop accelerating so I decided to make a PID controller for the speed of the vehicle as well to get it to run at a more reasonable speed. I started with a value of 1 and decreased it by 50% until the car wasn\'92t breaking and accelerating too quickly. I realized that the higher the value of the Kp parameter for the speed controller, the more aggressive the vehicle breaked and stopped. After tuning the speed controller, the car was still overshooting when attempting to minimize the p error, so I next looked at the Kd term. Increasing the Kd term would cause the car to minimize the overshoot of the target. I started with a value of 1 and found that this was not enough. I doubled it until I found a more reasonable value. I found that a value of 4 did the job relatively well. At this point, the car was able to make it all the way around the track.


The effect of each of the PID coefficients was unsurprising and they worked pretty much as expected namely:
* The Kp coefficient increased the rate of correction of the steering angle
* The Ki coefficient caused the car to stay closer to the absolute center of the road
* The Kd coefficient caused the car to minimize the overshooting caused by the Kp coefficient.

If anything was surprising, it was the respective sizes of the coefficients. For the Ki coefficient, I didnt even need to increase it from zero, which in retrospect is probably because the bias of this simulator is likely very low. Additionally, I thought the Kp coefficient would need to be larger than the Kd coefficient because the Kp has a more direct effect on correcting the steering angle, but it seemed like, at least for this problem, a small value for Kp was sufficient

