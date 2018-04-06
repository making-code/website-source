+++
title = "Digital Circuits"
date =  2018-04-04T09:09:58+02:00
weight = 1
+++

When we work with computers, we mostly deal with digital rather than analog circuits.
The digital circuits in computers are electrical circuits that operate with two values:
**true** and **false**, or _yes_ and _no_.

Computers are digital circuits as they internally only work with those two values, usually referred to as **bits**.
A bit is a single value that is either true or false. 

By combining these bits and making the circuits fairly complex, we can use such digital circuits to solve a variety of problems - after all computers have proven to be quite powerful. But how does that work?

## Rephrasing the problem

First we need to rephrase the problem in a way that a digital circuit (e.g. a computer) can work with it.
For example the problem "Can I play computer games today?" might be rephrased to "Do I have nothing else on my schedule?"

That is a "Yes/No" question, so it can be answered with a digital circuit. Now we need to think of how we would represent a "yes" and a "no" answer.
Let's say we use a single light - if it turns on, we can play and if it doesn't, we can't play.

The digital circuit to answer our question is a power source (e.g. battery), the light (e.g. an LED with a resistor to limit the voltage) and a switch.
We can use the switch to input the answer to our question and the circuit will show us if we can play:

| Schedule free? | Switch | LED | Can we play computer games? |
| --- | --- | --- | --- |
| yes | on | on | yes |
| no | off | off | no |https://www.youtube.com/watch?v=feMwFuihX2o

Here is a working version of our digital circuit:

![An LED that turns on, if the switch is in "on" position](/img/content/foundations/Simple-Digital-Circuit-Simulation.gif?width=300px)

To avoid having to think of power sources, resistors and so on, there is an alternative way of illustrating digital circuits, often referred to as the "logical circuit".
Here is the same circuit in the logical circuit schematic:

![A logical circuit with a button toggling from zero to one and turning a light on and off](/img/content/foundations/Simple-Digital-Circuit-Logic.gif?width=300px)

## Solving more complex problems

The previous digital circuit was not very interesting, but admittedly simple. Let's think of a circuit solving a more complex problem.

We want to build a circuit that can answer if somebody can take the company car or not. Let's rephrase it as a few yes/no questions:

1. Are you old enough to drive a car?
2. Do you have a valid drivers licence?
3. Are you an employee of the company?
4. If you are not an employee, did somebody give you permission to take the car?
5. Is the car available at the desired time?

Alright, there's one important detail in there - question number four only needs to be answered (and answered with "yes"), if question number 3 has been answered with "no".
We could alternatively rephrase this as "Question three OR question four needs to be answered with yes".

Now that we broke the problem down into yes/no questions, we can design our digital circuit.

If we represent all questions 1-5 with switches again, we can only light up the "answer" light if questions one, two and five are answered and either three or four have been answered with "yes", so our circuit would look like this:

![A series of switches and an LED where two switches are in parallel, all others are in series](/img/content/foundations/Digital-Circuit-2-Simulation.gif?width=300px)

To explain the circuit, we can look at the questions again:

Old enough? | Drivers licence? | Employee? | alternative: Permission? | Car free? | Result |
| ----------| ---------------- | --------- | ------------------------ | --------- | ------ |
| no | doesn't matter | doesn't matter | doesn't matter |  doesn't matter | No |
| yes | no | d.m. | d.m. | d.m. | no | 
| yes | yes | no | no | d.m. | no | 
| yes | yes | no | yes | no | no | 
| yes | yes | yes | no | no | no | 
| yes | yes | no | yes | yes | yes | 
| yes | yes | yes | no | yes | yes | 

Looking at the table, we can formulate it this way: If Q3 **OR** Q4 are answered "yes" **AND** all other questions are answered "yes", we can take the company car.

The logical circuit is a lot less cluttered and represents the logic well:

![A logic circuit with five inputs, a four-input AND gate and a two-input OR gate connecting to a single light](/img/content/foundations/Digital-Circuit-2-Logic.gif?width=300px)

[For an interactive version, click here](https://simulator.io/board/zpiq7E0S3K/1).

In the logic circuit above, you see an input that is either "1" ("yes", on) or "0" ("no", off) for each question. This is where we put our answers in.

The answers for Q3 and Q4 go into a kind of switch that only outputs true ("yes"), if **at least one** of the inputs is true. Then, this output and all the other questions go into a switch that only outputs true ("yes"), if **all** inputs are true.

These two switches are called **gates**, in this case they are an _OR_ and _AND_ gate, specifically.

{{% notice note %}}
Such gates (and other types of gates) can be built with transistors, which is why the amount of transistors that fit into a processor matters - more transistors = more gates = more things it can do in a single step.
{{% /notice %}}

We have seen, that both the logical circuit and the "real" circuit behave identically, so we can use either tool in different stages:

* When we need to figure out the _logic_ (i.e. for which input combination our output is true and false), we can use the logic circuit to find our solution. Such a tool could be [simulator.io](https://simulator.io)
* When we need to build the real electrical circuit in hardware, we can use the circuit schematics to build the circuit based on what we have found out in the logic circuit. We can use tools such as [TinkerCAD](https://tinkercad.com) for this

Now that we understand how digital logic works on a circuit level, we can move to software and binary logic (true and false, 1 and 0). This is called [boolean logic](../boolean-logic/) and is discussed in the next section.