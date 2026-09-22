# damped-pendulum-simulation
A pendulum is a device that consists of a weight suspended from a pivot by a string or rod. It is a simple system that involves simple harmonic motion and oscillations. This project aims to mathematically model a pendulum, finding analytical solutions where applicable and numerical general solutions. The pendulum system is first idealised, then damping is introduced. The effects of linear and quadratic damping are compared. 

## Assumptions
- Pendulum bob treated as a point mass.
- Rod/string is massless and rigid.
- Pivot is fixed.
- Gravity is constant.
- No friction at the pivot.
- For the damping models, the resistive force is assumed to depend on angular velocity.

The equation of motion of the pendulum is derived from Newton's second law.

$$
\ddot{\theta} = -\frac{g}{L}\sin(\theta)
$$

**Where:**

*   $\ddot{\theta}$ is angular acceleration
*   $\theta$ is angular displacement
*   $g$ is gravitational acceleration
*   $L$ is the length of the rod/string

Angular displacement, $\theta$ is measured from the pendulum's equilibrium position in radians. ($\theta > 0$ represents a clockwise angle, and $\theta < 0$ represents an anticlockwise angle). 

Angular velocity, $\omega$ is the rate of change of angular displacement. It is positive when the pendulum is moving away from its equilibrium point, $0$ when it is at its turning point, and negative when it is moving towards its equilibrium point.

This equation shows that there is acceleration towards the equilibrium point. This is the restoring acceleration.

## Idealised Pendulum Solution 
For small angles, $\sin{\theta} \approx \theta$ is applied. $$\ddot{\theta} = -\frac{g}{L}\theta$$ is a linear ODE and has an analytical solution. 

<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/4dbf6935-e12e-4a68-9f32-8e301e9f83eb" />

To find a general solution, a numerical method is used. Euler's method approximates ODEs that do not have an analytical solution by taking small, discrete steps along tangent lines. 
$\omega  = \dot{\theta}$ and
$\dot{\omega} = \ddot{\theta}$

$\dot{\omega} = -\frac{g}{L}\sin(\theta)$

Using Euler's Method, we have that

$$\theta_{n+1} = \theta_{n} + \Delta t (\omega_{n})$$

$$\omega_{n+1} = \omega_{n} + \Delta t (-\frac{g}{L}\sin(\theta_{n}))$$

## Ideal Pendulum Results
<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/901e3ff0-5ffb-41b3-81c7-eeee9bb524d4" />
<img width="567" height="454" alt="image" src="https://github.com/user-attachments/assets/3eab7ca4-f5d3-4a10-ac9e-a7ce033fbdb1" />

An initial value of $30°$ is chosen, along with a timestep of $0.01s$. This timstep introduces error, which can be reduced by taking smaller timesteps. This error causes the total energy of the system to increase over time due to accumulated error, also resulting in the amplitude of oscillations increasing as kinetic energy is increased after each oscillation. 

##

Euler's Method says that 
$$\theta(t + \Delta t) \approx \theta(t) + \dot{\theta}(t)(\Delta t)$$

The exact value should be $$\theta(t + \Delta t) = \theta(t) + \dot{\theta}(t)(\Delta t) +\frac{\ddot{\theta}(t)}{2!}(\Delta t)^2  + ...$$


This leaves out the terms behind which are proportional to powers of $\Delta t$. 
The error is $\frac{\ddot{\theta}(t)}{2!}(\Delta t)^2  + ... $

Therefore, by choosing smaller values of $\Delta t$, the error gets smaller.

<img width="858" height="392" alt="image" src="https://github.com/user-attachments/assets/02e2de08-982f-446e-82fb-e8aceed84c68" />

## Limitation of the Small Angle Approximation

<img width="618" height="454" alt="image" src="https://github.com/user-attachments/assets/df23a14a-d926-4060-bc83-58cddd82c57d" />

<img width="618" height="454" alt="image" src="https://github.com/user-attachments/assets/b51cab82-069a-41d9-93d0-5b83f59994c1" />

<img width="618" height="454" alt="image" src="https://github.com/user-attachments/assets/8db40eb8-6692-412f-ad74-7e72249760c2" />

<img width="618" height="454" alt="image" src="https://github.com/user-attachments/assets/4ce08e21-2d67-4d49-8c46-469a35d57a29" />

Using the small angle approximation, the period $T$ is independent of the maximum angle. 
$T \approx 2 \pi \sqrt{ \frac{L}{g}}$ 

Hence, the period observed from the graphs of the small angle approximation is equal for all initial angular displacement values chosen, which it is not equal for the numerical solutions. As the initial angle increases, this difference in period becomes larger and accumulates over successive oscillations. 

## Linear Damping

It is assumed that the damping is due only to drag/ air resistance, and opposes the pendulum's motion. Hence, it is a force that acts tangential but opposite to the motion of the pendulum. For linear damping, drag force, $F_d$ is assumed to be proportional to the tangential velocity of the pendulum.
$F_d \propto v$

$$F_d = -b L \omega$$ where $b$ is the _damping coefficient_

The equation of motion of a linearly damped pendulum is $$\boxed{ mL \dot{\omega} = -mg\sin(\theta) - bL\omega }$$

<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/2b677cf8-b7ae-4aff-8bb7-7cd27b0ecaa0" />

## Linear Damping (Small Angle Approximation)
For small values of $\theta$ , $\sin(\theta)$  can be approximated with $\theta$. $\sin(\theta) \approx \theta$.

Therefore, the new equation of motion is
$$mL \ddot{\theta} = -mg\theta - bL\dot{\theta}$$
$$\ddot{\theta} + \frac{b}{m}\dot{\theta} + \frac{g}{L}\theta = 0$$

This is a homogeneous second-order linear differential equation and can be solved analytically.

## Quadratic Damping 
The drag force, $ F_d $ is assumed to be proportional to tangential velocity. $$F_d = kv^2$$ where $k$ is the _damping coefficient_.
$$F_d = k L^2 \omega^2$$ 



The force will be rewritten as 
$$F_d = - kL^2 \dot{\theta} |\dot{\theta}|$$ to preserve direction. This makes it so that $F_d$ is negative for positive $\omega$ and positive for negative $\omega$

$$\boxed{ mL \ddot{\theta} = -mg\sin(\theta)  - kL^2 \dot{\theta} |\dot{\theta}| }$$

<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/ce05a931-aaf7-4be4-b41a-26790cfdaf1b" />

## Comparison of Linear and Quadratic Damping

<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/80ff043f-171c-4984-b366-5f1d62cb41de" />

<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/c4558a11-4663-4c8d-8ebc-174e4e63d19d" />

There is more difference as t gets larger. This relationship is significant because $|F_d| \propto |\omega|$ for linear damping and $|F_d| \propto |\omega|^2$ for quadratic damping, Hence, damping force should decrease more signifincantly for quadratic damping when $\omega$ decreases, and this is observed in the graph as the decrease in the amplitude of the waves is more prominent in the graph of linear damping.


<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/bce9cfcd-e436-4134-91bd-c4d997c05470" />

For linear damping, $F_l = bL\omega$. As the pendulum reaches a turning point, $\omega \to 0$, $F_q$ approaches 0 faster than $F_l$ because $F_q \propto \omega^2$. $\omega ^2$ approaches $0$ faster than $\omega$ does.


<img width="579" height="454" alt="image" src="https://github.com/user-attachments/assets/1d9e7845-6fd9-40fd-b9c7-1932e6011340" />

<img width="567" height="454" alt="image" src="https://github.com/user-attachments/assets/122d0faa-aefd-4a86-a4c3-d00ad0fe3d2b" />

The flattening effect of this graph is because as $\omega$ approaches $0$,  $\omega \to 0$ and $\frac{dE}{dt} \to 0$

## Period 
A period is the interval of time between consecutive events. In this case, the period is the time taken for one complete oscillation. We can measure it as the time between peaks (high points) or troughs (low points) in the graph of angular displacement against time. 
When measured, 

Linear damping: 2.018

Quadratic damping: 2.018

Theoretical period: 2.006

Damping significantly reduces the amplitude and energy of the pendulum, but for the damping coefficients used in this simulation, it has little effect on the period.

## Limitations

- Euler's method introduces numerical error.
- Accuracy of results depend on timestep.
- Damping coefficients were chosen rather than experimentally measured.
- The model simplifies real-world air resistance.
- The small-angle approximation is only valid for sufficiently small angles.


## Conclusion 
Using numerical methods, a pendulum can be effectively modeled using Euler's Method which is a simple method. Accuracy of the model depends on the timestep chosen for the model. Choosing a smaller timestep reduces error. The small angle approximation is less accurate when using it for larger initial angular displacment. Introducing damping reduces the energy of the system and subsequently the amplitude of oscillations, while leaving the period relatively unchanged. Linear and Quadratic Damping are dependent differently on the velocity, and produce different effects. 


Different damping coefficients can be chosen to produce different results, with larger damping coefficients leading to more effective damping, causing the amplitude of the oscillations to decrease quicker. With larger initial angles, the path of the pendulum should largely remain unchanged but small angle approximations can no longer be used and the path of the pedulum may diverge from the path of a small angle approximation. This model uses a similar methodology to the models of more complex concepts, such as orbital mechanics and a two-body system, similarly involving differential equations and finding a numerical or analytical solution.

## References 


(https://math.libretexts.org/Courses/Monroe_Community_College/MTH_225_Differential_Equations/03%3A_Numerical_Methods/3.01%3A_Euler's_Method)

(https://web.physics.ucsb.edu/~lecturedemonstrations/Composer/Pages/40.37.html)

(https://math.libretexts.org/Bookshelves/Scientific_Computing_Simulations_and_Modeling/Scientific_Computing_(Chasnov)/II%3A_Dynamical_Systems_and_Chaos/10%3A_The_Simple_Pendulum)

(https://commons.erau.edu/cgi/viewcontent.cgi?article=2483&context=discovery-day)

(https://math.libretexts.org/Bookshelves/Differential_Equations/Introduction_to_Partial_Differential_Equations_(Herman)/12%3A_B_-_Ordinary_Differential_Equations_Review/12.02%3A_Second_Order_Linear_Differential_Equations)

(http://maeresearch.ucsd.edu/~vlubarda/research/pdfpapers/EJP_21.pdf)

(https://phys.libretexts.org/Bookshelves/University_Physics/University_Physics_(OpenStax)/Book%3A_University_Physics_I_-_Mechanics_Sound_Oscillations_and_Waves_(OpenStax)/15%3A_Oscillations/15.06%3A_Damped_Oscillations)
