# 04 Challenges - For Nerds (Putting it all together!)

In a real spacecraft like SunbYte, subsystems don't operate in isolation. The thermal management system and the solar array positioning system have to communicate. 

If you have finished Activity 2 early, your final challenge is to combine everything you have built today into one ultimate, integrated system. You will need to wire both the **Thermistor circuit** from Activity 1 and the **Servo/Potentiometer circuit** from Activity 2 onto the same breadboard.

You will have to write the code for this from scratch! Here are your goals, broken down into stages:

## Challenge 1: The Sweeping Array
Right now, your servo jumps to whatever position the dial dictates. 
**The Goal:** Write a program that makes the servo automatically "sweep" (oscillate) back and forth from 0 degrees to 180 degrees, over and over again, simulating a radar or a solar array searching for the sun.
*Hint:* You will need to use variables to keep track of the current pulse width, and slowly increase or decrease it inside your `loop()`.

## Challenge 2: Speed Control
**The Goal:** Program the Arduino to read your potentiometer dial, but instead of using it to control the *position* of the servo, use it to control the *speed* of the sweep!
*Hint:* You can `map()` the potentiometer's 0-1023 reading to a value between 1 and 50. Use this calculated number as a `delay()` between each tiny step of your servo's movement.

## Challenge 3: Thermal Safety Cutoff
Motors draw a lot of power. If the spacecraft gets dangerously cold, we need to shut down all non-essential movement to save power for the heaters.
**The Goal:** Read the thermistor on analog pin `A0`. Wrap your servo sweeping code in a giant `if/else` statement. 
* If the temperature is "safe" (above your target threshold), the servo sweeps normally.
* If the temperature drops into the "freezing" zone, the servo immediately stops moving and holds its current position. (To test this, simply let go of the thermistor so it cools down to room temperature).

---
*Once you are completely done and have shown off your integrated system, please make sure to unplug your Arduino, neatly pack up all your components, and let an organizer know you've completed the workshop! Great job!*
