---
layout: post
title: "Legolas, the basketball playing robot."
modified:
excerpt: "Its aim was sturdy and true, 8 out of 15 times."
comments: true
tags: []
---

*One of my favorite classes at school was in mechatronics. It was a two-part, project-based 
course; the first half was intensive lectures - focusing on state diagrams, circuit design,
RC performance and signal processing, motors, etc - and the second half was an applied project.
Our goal was to play basketball against a brick, and win. For the sake of our pride, thankfully
we did. :)*

*A summary of the project is below, and a more detailed description (layouts, schematics, source code, etc) 
of the project can be found [at this site][1].*

## Background 

I was paired up with a great team of folks - Mason, Armelle, and Sid - who were ME & design students
at Stanford. 

The very first thing we did was name our team "The Fellowship" because we knew it would be a long, 
arduous journey. We also named our robot "Legolas", since we wanted it to be an admirable shooter. 
There may or may not be many Lord of the Rings jokes in this post.

<figure>
	<img src="/images/legolas_the_team.jpg">
	<figcaption>Citizens of The Shire.</figcaption>
</figure>

Technically, our workstream could be divided into roughly three sections:

* Mechanical Design
* Electrical Systems
* Software

## Mechanical Design

<figure>
	<img src="/images/beautiful_legolas.jpg">
	<figcaption>The proud archer Legolas. As you can see, we used a two leveled approach.</figcaption>
</figure>

We used a two-tier design, with considerations regarding motor placement, sensor mounting,
space for the electrical components, and the ability to effectively "catch" and shoot the balls.


### *Motor Requirements*

We noticed that as we added a second layer to our bot, the movement of the bot began to be 
severely effected and its turning was ineffective. We determined that our motors did not have 
enough torque to power our bot. We had done a lot of ground testing with one layer and only second 
layer testing with the bot resting on a tissue box (wheels off the ground) so we didn't catch this 
until late into our build. We also used the provided driver board (the one with both enable and direction 
outputs) to control their respective speeds. So we upgraded our drive motors to those that were slower but 
provided more torque. We were then to get pretty accurate control of each wheel. 


### *Electrical Components & Sensors Mounting*

We used the following electrical components/sensors in our design: arduino uno, voltage regulators, 
L293 motor driver, DS3658 motor driver, bumper sensor, hi-tec servo, and photo transistor (with 
circuits to convert to an IR sensor). We placed all electrical components (including all breadboards) 
except for the servo and IR sensor, on the first level (model shown below). The bumper sensor was screwed 
down in one of the 6 bumper slots. The large holes were used for battery cables to run to the power supply 
circuit. In addition, some of these holes were used for the motor cables to attached to the driver/power 
circuits/arduino. All the very small holes were used to mount the driver and arduino in place (breadboards 
were glued down). There are a lot of them because that gave us the flexibility to move them.  

The servo was mounted on furnished parts from RoboTerra (blue plates on picture above). The IR sensor 
breadboard was mounted (vertical-wise) to a carriage that hung from our second level.

### *Catching & Shooting System*

We implemented a flywheel system to shoot on the two point basket. With the help of the IR sensor, 
Legolas would drive around and aim in the correct direction for the fixed flywheel position to shoot. 
Once Legolas stopped, the flywheels would activate and balls would be shot at one second intervals towards the hoop.

### *Catching/Storage*

When the BRB sensor on the playing field was hit, one of the fellowship would drop balls into a tube 
for ball collection. The tube was 2+1/4" pvc pipe with the top half cut off. It was angled at approximately 
30 degrees downwards. We placed a duron backing in the tube (so no balls would fall out during movement) and 
used the top of a plastic cup as a funnel in order to make placing the balls into the tubes easier. A servo 
gate held the balls in position. 

### *Ball Dispensing*

As mentioned above, we mounted a servo with a long metal rod as a gate for the balls. The balls would 
rest at the gate until the time to shoot. The servo would quickly open and close, allowing only one ball 
to go into the flywheel shooter at a time. The servo would pause for one second between balls to allow 
the flywheel to resume nominal speed. 

### *Flywheel Mechanism*

To power our flywheels, we used two Jameco DC motors (found in the 210 supply closet) attached to 
large lego wheels. We found this to work well as the rubber wheels were able to spin fast with 
significant inertia. The two motors were mounted on  a duron board using laser-cut mounts. The motors 
were screwed into the mounts, with one mount having a slider to move its motor an inch in either direction. 
This allowed us to easily tune the separation between the flywheels. The flywheel plate was then mounted 
at a 50 to 60 degree angle (based on trial and error).  We used a provided motor driver and had the 
voltage supply to flywheels at around 5V. 

## Electrical Systems

The electrical system included an IR Beacon sensor, a bumper switch, a shooting mechanism,
the motors, and general power management. I'll walk through our process for the IR sensor
below and share the schematic for our power system.

### *Arduino Pin Connections*

<figure>
	<img src="/images/arduino_pin.png">
	<figcaption>Cheap microcontrollers, courtesy of Italy.</figcaption>
</figure>

### *IR Beacon sensor* 

We designed one IR sensor to detect the 2-point basket, which outputs a 3kHz IR signal. This 
sensor has several stages, as shown below. Through these stages the circuit picks up IR light, 
filters out extraneous frequencies, amplifies the signal and converts it from analog to digital 
to be read by an Arduino.

<figure>
	<img src="/images/complete_circuit.jpg">
	<figcaption>The complete circuit.</figcaption>
</figure>

Legolas runs off a single supply voltage (2 batteries in series) so we offset the IR circuit 
voltage with a virtual ground. To allow for a range of IR signals we set the offset voltage close 
to the 5V positive supply voltage of the circuit.

1. *Transresistive Circuit* - An LTR-3208 phototransistor outputs current proportional to the 
intensity of light incident on it. This current goes to the virtual ground through the transresistive 
circuit. The chosen LM6144 op amp allows the output voltage to go all the way down to ground before railing.
2. *High Pass Filter* - We used a high pass filter designed to attenuate the 120 Hz noise from indoor 
lighting. We also did this stage before amplifying the signal to prevent noise amplification. Our corner 
frequency was calculated to be ~482 Hz.
3. *Amplifier* - We used the LM6144 quad op amp chip from the transresistive circuit, in a non-inverting 
configuration, to amplify the filtered signal with a gain of 21. This gain was chosen based on testing the 
circuit at similar distances to what are experienced during the bot's actual run. We were able to have a 
peak to peak output amplitude of 4.5V, giving us the ability to fine tune our detection thresholds.
4. *Low Pass Filter* - A low pass filter was implemented to keep out any high frequency noise that 
may result from the other electronics on the bot, and specifically the four DC motors used for the 
drive train and fly wheel mechanism. We used a corner frequency one order of magnitude higher than 
the IR beacon frequency.
5. *Schmitt Trigger* - In the final stage of the circuit we used a Schmitt trigger to reduce the effect 
of noise and also to keep the comparator in the on state for a longer duration of time before turning off 
again. This also ensures the Arduino will be able to detect the circuit low output, because a longer 
fraction of the period is spent in the low state.

### *Power Circuit*

<figure>
	<img src="/images/power_circuit.jpg">
	<figcaption>Don't underestimate how important the fuse next to the switch is :).</figcaption>
</figure>

Our power circuit provided two output voltages: one at 12V and one at 5V. We included a 1A fuse at the
 battery connection to protect the robot's electronics, and a switch to turn power on and off. An 
 adjustable voltage regulator was used to provide 12V for the Arduino and drivetrain motor driver, and 
 a fixed 5V voltage regulator was used to power the sensors, servo and flywheel motor driver.

## Software

Our software code was exclusively designed to "beat the brick." We decided that we wanted to shoot 
for 2 point baskets, and that it would be a good idea to have our robot (Legolas) "reset" multiple 
times in 2 minutes to increase the probability that we would make at least one basket. We thought 
that, if the robot's original location was not accurate, that it would be more prudent/risk-adjusted 
to "break" the connection and reset with the basket again. 

With this in mind, our robot made good use of timers and very simple external signals - one bumper 
on the front, and an IR sensor. We coded our bot to drive forward and hit the wall separating the 
two courts. After then, it performed an infinite loop of bumping against the BRB three times to 
request balls, and then strafing back and forth along the wall. The robot would stop to shoot if 
the IR was triggered; if not, then we calibrated the robot to stop where we expected the basket to be. 

To shoot, we had three balls that were held behind a partition. This was controlled by a servo motor. 
Our balls would be shot by two flywheels - Lego wheels attached to motors. With regard to software, 
when the robot was in its "shooting state," the flywheels would be activated and the servo motor was 
timed to allow balls to be shot in 1sec increments. We found that the process of shooting actually 
took a significant amount of inertia away from the Lego wheels, and as a result, we needed to give 
the motor time to allow the wheels to return to full speed.

### *State Diagram*

Our code looped through two primary functions: a case checker (LegolasCASE) and an event checker 
(LegolasEVENTchecker). Our state diagram, which is reflected in the case checking function, consists 
of two nested switch-case statements. The diagram below, shows the master state diagram - the higher 
level logic that dictates how the robot will perform at all times. 

<figure>
	<img src="/images/state_diagram.png">
	<figcaption>The brain of our operation.</figcaption>
</figure>

Within each state/case in the master diagram, there may be smaller activities: for example, in the 
"Shooting Search" state, the robot will drive in reverse, stop, drive forwards, and search for an 
IR trigger. Our final code can be found on my Github page, [here][2].

## Lessons Learned!

Yes, we definitely learned a lot. In future mechatronic work (my hope is to volunteer with 
the local Mountain View HS [FRC][3] team!), these will be some important considerations:

* **Give yourself slack in early HW designs.** We redesigned our drivetrain 4 or 5 times, and 
each new design cost us a lot of time since laser cutters were in short supply. A few specific 
highlights: make sure your holes are large enough to fit a battery molex through. Random holes 
are helpful, but an "accordion" design (long slats) hurts the structural integrity of the board. 
To manage disparity between two motors, use high-torque motors for faster acceleration.
* **Cleanliness really matters.** When you first start, organize your bin (or workstation) 
between your different components/types of components/systems. As you redesign, you will end up
 with a lot of scrap parts, random nuts, random screws, etc. This can make a pretty gnarly nest 
 of used goods (and you will lose things) if it is not managed well.
* **Develop good support systems.** Try to give yourself the opportunity to fail as quickly as 
possible. Many things will go wrong, but the amount of time it will take to fix is a function 
of your support systems. Schematics are helpful. Designing an exploded assembly (and all components - including 
casters and motors) prevents small mistakes. A state diagram and pseudo-code tighten up 
the logic. In the same vein, have an early conversation with your coach about when and how to 
ask for support.

It was also a ton of fun - if you have any questions, thoughts, or ideas for future projects,
please let me know! :)

[1]: http://the-me210-fellowship.weebly.com/
[2]: https://github.com/brad-svds/Legolas
[3]: http://www.firstinspires.org/robotics/frc