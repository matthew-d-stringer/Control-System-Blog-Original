# Introduction to System Modeling using Differential Equations

## Intro

Mathematical Models are fundamental to the design of feedback control systems.
Control systems engineers rely on accurate mathematical models to properly understand how a system behaves and design optimal feedback mechanisms.
Differential equations most often represent mathematical models of systems.
Thus, the analysis of control algorithms is frequently identical to the analysis
of differential equations.

There are two modeling and analysis approaches in use for linear systems: 
frequency-domain approach, and state-space approach. 
Both of these methods are based on concepts taught in an Ordinary Differential 
Equations class.
This section will primarily focus on creating models of systems using the 
state-space approach.

## What makes up a differential equation
A differential equation is an equation consisting of function $y(t)$ and its
derivatives. 
$$
y^{(n)}(t) = f\left(t, y(t), y'(t), \cdots, y^{(n-1)}(t)\right).
$$
In mechanical systems, these functions often correspond to position ($x$), 
velocity ($v$) and acceleration ($a$), where
$$
v(t) = \frac{d}{dt}x(t) \text{ \quad and \quad } a(t) = \frac{d}{dt}v(t).
$$
However, this may not be the case. 
In more complicated systems, a model may consist of a system of differential
equations. 
If the model consists of two functions, $y_1, y_2$, then it will take the form:
$$
y_1^{(n)}(t) = f\left(
    t, 
    y_1(t), y_1'(t), \cdots, y_1^{(n-1)}(t), 
    y_2(t), y_2'(t), \cdots, y_2^{(n-1)}(t)
\right),
$$
$$
y_2^{(n)}(t) = g\left(
    t, 
    y_1(t), y_1'(t), \cdots, y_1^{(n-1)}(t), 
    y_2(t), y_2'(t), \cdots, y_2^{(n-1)}(t)
\right).
$$
The functions $y_1, y_1', \dots, y_1^{(n-1)}, y_2, y_2', \dots, y_2^{(n-1)}$
are called the *state* of the system. 
This is because knowing the values of these at a specific time 
allow you predict the future behavior of the system (assuming you know the dynamics).
You may notice that $y_1^{(n)}, y_2^{(n)}$ are not considered state variables. 
This is because these values can be solved for by knowing the other values.

As you may notice, these forms of differential equations are pretty general, 
and unfortunately, mathematicians have yet to determine general solutions for 
any of these.
Thus, for our purposes, we will instead look at a simpler form of model,
the Linear Time-Invarient (LTI) System.

## The Linear Time-Invarient System

LTI systems are differential equations with two constraints: 
Linearity (aka superposition), and Time-invarience.

Time-invarience means that whenever the system has a specific state, it will
always behave the same regardless of the specific time.
In other words, time-invarience means that time does not affect the dynamics of
the system.

Linearity means that given any two particular solutions 
$$y_1 = f(t) \text{\quad and \quad} y_2 = g(t)$$,
the following are also solutions to the system
$$f(t) + g(t) \text{\quad and \quad} cf(t).$$

In effect, these conditions restrict the form of the differential equations:
$$
y^{(n)}(t) = \alpha_1 y(t) + \alpha_2 y'(t) + \cdots + \alpha_{n-1} y^{(n-1)}(t),
$$
where $\alpha_i$ are constants.
For systems of differential equations, the form is similar:
$$
y_1^{(n)}(t) = 
    \alpha_{11} y_1(t) + \alpha_{12} y_1'(t) + \cdots + \alpha_{1(n-1)} y_1^{(n-1)}(t) 
    + \\
    \alpha_{21} y_2(t) + \alpha_{22} y_2'(t) + \cdots + \alpha_{2(n-1)} y_2^{(n-1)}(t)
    ,
$$
$$
y_2^{(n)}(t) = 
    \alpha_{11} y_1(t) + \alpha_{12} y_1'(t) + \cdots + \alpha_{1(n-1)} y_1^{(n-1)}(t) 
    + \\
    \alpha_{21} y_2(t) + \alpha_{22} y_2'(t) + \cdots + \alpha_{2(n-1)} y_2^{(n-1)}(t)
    .
$$