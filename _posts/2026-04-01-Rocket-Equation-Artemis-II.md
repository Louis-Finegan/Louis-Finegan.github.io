---
layout: post
title: "It <em>Is</em> Rocket Science Part I: Artemis II and the Rocket Equation"
subtitle: "Today is launch day of the Artemis II mission, the first crewed mission to orbit the Moon and back. This marks a new chapter of human space exploration, building on decades of progress since the Apollo era. In this post, we will focus on the physics that makes these missions possible, by deriving the rocket equation."
background: /img/posts/Rocket-Equation-Artemis-II/artemis-ii-rollout.jpg
imagecredit: <a href="https://www.nasa.gov">NASA</a>
---


Today, April 1<sup>st</sup> 2026, is an important day for space travel with the launch of Artemis II. At 6:24p.m. (Eastern time, ET) or 11:24p.m. (Irish Standard time, IST), the Artemis II rocket, carrying the Orion spacecraft with a crew of four, will launch from the Kennedy Space Center in Cape Canaveral, Florida, on a mission to orbit the Moon and return. 

The major difference from the Apollo missions back in the 1960s and 1970s is that we intend on not just to visit the Moon, but to establish a sustained presence there, using it as a stepping stone for future space missions. 

Artemis II will test the Space Launch System (SLS) and the Orion Spacecraft with a human crew to ensuring all systems are ready for a future Moon landing intended for 2028. The crew consists of, Commander Reid Wiseman, Pilot Victor Glover, Mission Specialist and first woman to leave low earth orbit Christina Koch and first non-U.S. Citizen to leave low earth orbit Jeremy Hansen.

Dispite the excitement of this launch, there is a great opportunity to talk about some physics. Specifically, to answer the question of how do rockets actually move?

## How Rockets Move

Rockets carry their own fuel and eject it at a high velocity in one direction. We know from Newton, that every action has an equal and opposite reaction. As the exhaust gases are expelled downward, the rocket experiences an equal and opposite force that propels it upward.

At the same time, the rocket is losing mass by expelling its fuel. This means that if we want to accelerate to a particular velocity, the amount of fuel required becomes an important factor. It also leads to important design decisions about payload mass, since carrying additional mass requires more fuel, which in turn increases the total mass that must be lifted and accelerated.

In this post, we will derive a relation between the mass and velocity of the rocket using basic physics principles. This relationship is known as the rocket equation. 

## The Rocket Equation

The following figure shows a rocket in two frames, $\Delta t$ apart. In the first frame, the rocket has a mass $m$ and is moving with velocity $v$. In the second frame, the rocket has ejected fuel with mass $\Delta m$ and, the rocket has lost mass and, in turn, gained velocity $\Delta v$.

![Image by Author](/img/posts/Rocket-Equation-Artemis-II/rocketdiagram.jpg)

The net force exerted on the rocket is expressed as the change in momentum $\Delta p$ in that change in time $\Delta t$

$$F = \frac{\Delta p}{\Delta t} = \frac{p_{\Delta t} - p_0}{\Delta t}.$$

At the initial time $t = 0$, the rocket has a mass of $m$ and is moving with a velocity $v$, so the momemtum $p_0 = mv$. However, after a short time $\Delta t$, the rocket has ejected fuel with velocity $u_e$, and the rocket has gained velocity $\Delta v$. The momentum at $t = \Delta t$ can be written as

$$p_{\Delta t} = (m - \Delta m)(v + \Delta v) + \Delta m u_e.$$

We can go a step further by noting the exhaust velocity $u_e$ is measured relative to an observer on the ground. From the rockets frame of reference, the exhaust velocity is

$$u_e^{\rm rocket} = u_e - v.$$

Combining this and the momentum becomes

$$p_{\Delta t} = mv + m\Delta v - \Delta m \Delta v + \Delta m u^{\rm rocket}_e.$$

Since the time that has elapsed between these two frames is small, only a small amount of mass has been ejected from the rocket and only a small change in velocity occurs. Therefore, it is reasonable to assume $\Delta m \Delta t \approx 0$. Hence, the net force is

$$F = m\frac{\Delta v}{\Delta t} + \frac{\Delta m}{\Delta t}u^{\rm rocket}_e.$$

If we take the limit as $\Delta t \rightarrow 0$, we obtain the differential form

$$F(t) = m(t)\frac{d v}{d t} + \frac{d m}{d t}u^{\rm rocket}_e.$$

Now it's a good time to talk about external forces. If the rocket was in deep space, or even high earth orbit, it could be safe to say (for the purpose of example) that external forces such as gravity or drag would not be a big issue. So we can ignore them, setting the net-force $F(t) = 0$. The differential equation simplifies drastically to

$$m(t)\frac{d v}{d t} = - \frac{d m}{d t}u^{\rm rocket}_e.$$

Let's also assume that the fuel is ejected from the rocket at a constant rate oveer time. By that assumption the differential equation easy to solve analytically, leading to the solution:

$$\Delta v = v(t) - v_0 = u^{\rm rocket}_e\ln{\frac{m_0}{m(t)}},$$

where, $v_0$ is the velocity and $m_0$ is the mass of the rocket at $t=0$. $m(t)$ is the mass of the rocket at time $t$, which can yield the change in velocity at time $t$ for its initial time. 

This equation is a famous equation known as the ideal rocket equation creditied to the Russian rocket scientist, Konstantin Tsiolkovsky in 1903. Although it has been first derived  by British mathematician William Moore in 1810. 

The ideal rocket equation is great description for a rocket in outside of low earth orbit, where gravity and drag forces do not have much influence. What does the model look like when we account for these external forces. 

The gravitational force on earth is given by $F_g = -mg$, where the gravitational acceleration on earth $g \approx 9.81 \rm ms^{-2}$. The drag force $F_d \propto -v^2$. Including these forces give the following non-linear differential equation:

$$ m(t)\frac{d v}{d t} + \frac{d m}{d t}u^{\rm rocket}_e + m(t)g + kv^2 = 0, $$

where $k$ is a proportionality constant. 

Unfortunately, due to the nonlinearity of this equation, we are generally forced to resort to numerical methods to solve it. Despite the added complexity, it provides a more accurate description of a rocket launch from earth.

## Conclusion

Over the next ten days, as Artemis II lauches and the Orion spacecraft travels on its trajectory to the Moon and back, its motion can be understood throught the lens of the rocket equation&mdash;paving our journey back to the Moon and then onto Mars.
