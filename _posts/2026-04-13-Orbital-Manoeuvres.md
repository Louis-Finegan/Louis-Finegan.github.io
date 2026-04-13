---
layout: post
title: "It <em>Is</em> Rocket Science Part III: How to get to the Moon"
subtitle: "Now that the Artemis II crew have safely returned from their ten-day voyage to the Moon, we explore the physics of actually getting there. Using orbital mechanics, we demonstrate how a spacecraft can perform orbital manoeuvres to change its trajectory between the Earth and the Moon. We then  apply this to a simplified transfer orbit in a simulation similar to that of the Lunar Reconnaissance Orbiter."
background: /img/posts/Orbital-Manoeuvres/Eclipse.jpg
imagecredit: <a href="https://www.nasa.gov">NASA</a>
---


It was an exciting week for space travel. After half a century, humans have finally left low Earth orbit and embarked on a trajectory to fly by the Moon and return safely to Earth. Along with breaking the record for the furthest distance humans have traveled from Earth, the Artemis II crew captured some awe inspiring photographs of the Lunar surface and of Earth from the Moon's perspective. These include images of Earthrise, detailed views of the lunar surface and even a solar eclipse. These photos and more can be found on the [NASA website](https://www.nasa.gov/artemis-ii-multimedia/).

![From NASA at https://www.nasa.gov/image-detail/amf-art002e009289](/img/posts/Orbital-Manoeuvres/Earthrise-NASA.jpg)

> Image by [NASA](https://www.nasa.gov/image-detail/amf-art002e009289)

For the Artemis II crew to capture these photographs, they first had to reach the Moon. To achieve this, the spacecraft relies on the gravity from the Earth and the Moon, along with its engines to adjust its trajectory. This is made possible through *orbital mechanics*.

In this post, we will not reproduce the Artemis II trajectory, which was explored in [*part II*](https://louis-finegan.github.io/2026/04/06/Artemis-II-Analysis.html) of this series. Instead, we will consider the orbit similar to that taken by the [Lunar Reconnaissance Orbiter](https://en.wikipedia.org/wiki/Lunar_Reconnaissance_Orbiter) (LRO), launched in 2009 to map out the terrian, finding safe landing sites for future crewed missions. 

Additionally, we will constrain all trajectories to lie in a plane. This simplification allows us to constuct orbits that are easier to analyse and avoids the need for more complex manoeuv is to produce orbits that are simple and do not require too many complex manoeuvres.

## Orbital Mechanics

Orbiting the Earth is a bit like continuously falling towards it, except you never reach the ground. If you throw a ball tangentially to the Earth's surface, gravity will cause it to fall and hit the ground some distance away. If you throw it faster, it will travel further before hitting the ground. Now imagine, there were no buildings or trees in your way, and you throw ball with just the right speed, it will fall towards Earth. However, due to the curvature of the Earth causes the surface to fall away beneath it at the same rate. The result is that the ball never lands and it is in orbit. 

We can calculate this orbital velocity using 

$$v = \sqrt{\frac{GM}{r}},$$

where $G=6.6743\times 10^{-11}\rm m^{3}\rm kg^{-1} \rm s^{-2}$ is the gravitational constant, $M$ is the mass of the Earth and $r$ is the distance from the center of the Earth. 

Using this, we can estimate the velocity of an object in circular orbit from Earth. The Moon follows an almost circular orbit at a distance of $384,400\rm km$, giving

$$v_{\rm Moon} = \sqrt{\frac{GM_{Earth}}{r_{\rm Moon}}} \approx 1,022\rm m/\rm s.$$

A spacecraft in low Earth orbit (LEO), approximately $300\rm km$ above the Earth's surface, must travel faster: 

$$v_{\rm Spacecraft} = \sqrt{\frac{GM_{\rm Earth}}{r_{\rm Spacecraft}}} \approx 7,730\rm m/\rm s.$$

This higher velocity is required because the spacecraft is much closer to Earth, where the gravitational pull is stronger. As a result, it must have greater kinetic energy to remain in orbit and avoid falling back to Earth.

So far, this assumes perfectly circular orbits. In reality, the Moon's orbit is slightly elliptical. Does this make our calculation incorrect? Not significantly, the eccentricity is small enough that the circular approximation is sufficient for our purposes. However, elliptical orbits become essential when changing orbits. 

Altering an orbit requires changing velocity, which produces an elliptical trajectory. At a later point (typically at the apogee or perigee) another velocity can be applied to transition into a new orbit. This process is known as an orbital manoeuvre.

The following video illustrates such a manoeuvre. 

<video controls src="/img/posts/Orbital-Manoeuvres/Manoeuvres.mp4" title=""></video>

Initially, the satellite is in LEO. It performs a prograde burn (increasing its velocity), which raises it into a wider elliptical orbit. At apogee, a second prograde burn increases its velocity further, placing it into an even larger orbit. Finally, at apogee of this orbit, a retrograde burn (decreasing velocity) transitions the satellite into a smaller orbit.

For elliptical orbits, the Earth lies at one of the foci. Using this property, we can derive a more general expression for orbital velocity that depends not only on the distance $r$, but also on the semi-major axis $a$ of the ellipse:

$$v = \sqrt{GM\left(\frac{2}{r} - \frac{1}{a}\right)}.$$

This is known as the *Vis-viva equation* (Latin for "living force"), a term introduced by Isaac Newton.

## Lunar Reconnaissance Orbiter

To travel from LEO to a lunar orbit, we must determine the $\Delta v$ required to perform a prograde burn that places the spacecraft on a trajectory toward the Moon. This manoeuvre is known as a Trans-Lunar Injection (TLI)

The transfer trajectory is elliptical with $2a = r_{\rm Moon} + r_{\rm Spacecraft}$. Using the vis-viva equation, the required velocity is 

$$v_{\rm TLI} = \sqrt{GM\left(\frac{2}{r_{\rm Spacecraft}} - \frac{2}{r_{\rm Moon} + r_{\rm Spacecraft}}\right)} \approx 10,838.07\rm m /\rm s.$$

Thus, $\Delta v = v_{\rm TLI} - v_{\rm Spacecraft} \approx 3,108.07\rm m/\rm s$. Assuming gravity losses and other external forces are negligible, we can estimate the required fuel using the ideal rocket equation discussed in [*part I*](https://louis-finegan.github.io/2026/04/01/Rocket-Equation-Artemis-II.html) of this series. In the simulation, a slightly higher value of $\Delta v = 3,150\rm m/\rm s$ was used to ensure the spacecraft reaches the Moon's vicinity.

The animation below shows an example of a TLI relative to the Earth (blue) over a 100 day period. On day 0, the satellite (green) performs a prograde burn, placing it on a trajectory toward the Moon (grey). Upon arrival, a retrograde burn circularises the orbit at the altitude where the burn occurs.

<video controls src="/img/posts/Orbital-Manoeuvres/TLI-LRO.mp4" title=""></video>

The satellite enters lunar orbit after approximately 3 days and remains in a stable orbit for the remainder of the smulation.

A major challenge in this process is timing. If the TLI burn is performed too early or too late, the spacecraft will miss the Moon and instead return to Earth. To ensure interception, the burn must occur when the Moon is at the correct position in its orbit. This is quantified by the phase angle between the spacecraft and the Moon at the time of the burn. An angle of approximately $133.83^{\circ}$ is found to be optimal. 

## Conclusion

Reaching the Moon is not simply a matter of travelling in a straight line. Instead, it requires careful planning, timing and precise calculations. This becomes even more critical for crewed missions, such as Artemis II. 

Although we did not replicate the Artemis II trajectory, we still capture the core physical principles involved.

With the successful return of the Artemis II crew, there is renewed momentum and optimism that the next step is within reach: returning humans to the lunar surface once again, and this time to stay, before pushing onward to Mars.