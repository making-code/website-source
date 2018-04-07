+++
title = "Digital Circuits"
date =  2018-04-04T09:09:58+02:00
weight = 1
+++

When we work with computers, we deal with _digital_ rather than _analog_ circuits. They are electrical circuits that operate with two values: **true** and **false**, or _yes_ and _no_.

Computers only work with those two values, usually referred to as **bits**. A bit is a single value that is either true or false.

We combine 8 bits into bytes and create combinations to solve a variety of problems. But how does that work?

## Rephrasing the problem

First we need to rephrase the problem in a way that a digital circuit (e.g. a computer) can work with it.
For example we can rephrase the problem "Can I play computer games today?" to "Do I have nothing else on my schedule?"

That is a "yes/no" question, so  a digital circuit can answer it . Now we need to think of how we would represent a "yes" and a "no" answer.

Let's say we use a single light - if it turns on, we can play and if it doesn't, we can't play.

The digital circuit to answer our question could be a battery, the light and a switch. It might need a resistor, too so that the voltage through the light isn't too high.

We can use the switch to input the answer to our question and the circuit will show us if we can play:

| Schedule free? | Switch | LED | Can we play computer games? |
| --- | --- | --- | --- |
| yes | on | on | yes |
| no | off | off | no |https://www.youtube.com/watch?v=feMwFuihX2o

Here is a working version of our digital circuit:

![An LED that turns on, if the switch is in "on" position](/img/content/foundations/Simple-Digital-Circuit-Simulation.gif?width=300px)

We were thinking about batteries, resistors and so on, instead of the logic. To focus on the logic we can leave all those out and focus on the logic only.

Here is the same circuit in the logical circuit schematic:

![A logical circuit with a button toggling from zero to one and turning a light on and off](/img/content/foundations/Simple-Digital-Circuit-Logic.gif?width=300px)

## Solving more complex problems

The previous digital circuit was not very interesting, but pretty simple. Let's think of a circuit solving a more complex problem.

We want to build a circuit that can answer if somebody can take the company car or not. Let's rephrase it as a few yes/no questions:

1. Are you old enough to drive a car?
2. Do you have a valid drivers licence?
3. Are you an employee of the company?
4. If you are not an employee, did somebody give you permission to take the car?
5. Is the car available at the desired time?

We can see that question number four only matters, if the answer to question number 3  was "no".
We could rephrase this as "The answer to question three OR four needs to be yes".

Now that we broke the problem down into yes/no questions, we can design our digital circuit.

We can represent all questions with switches.
When answers one, two and five and at at least one of the questions three and four are yes we can turn the light on. In any other case the light will be off. Our circuit will look like this:

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

These two switches are so-called  **gates**, in this case they are an _OR_ and _AND_ gate.

{{% notice note %}}
Transistors or combinations of transistors represent logical gates in an electric circuit. That's why the amount of transistors that fit into a processor matters. <br>
More transistors = more gates = more things done in a single step.
{{% /notice %}}

Now we know how real digital circuits and digital logical circuits work. We have also seen that they behave identical and we can express a digital circuit as a logical one and vice versa.

Logical circuits and real circuits are useful for different situations:

* When we need to figure out the _logic_ (i.e. the behavior), we can use the logic circuit to find our solution. Such a tool could be [simulator.io](https://simulator.io)
* When we make hardware we need more detail. We need an electrical schematic, so we can use tools such as [TinkerCAD](https://tinkercad.com) for this

When programming, we care less about the electrical circuits.
In the next section we will discuss logic and operators on our values `true` and `false`. So read on to learn about [boolean logic](../boolean-logic/) in the next section.