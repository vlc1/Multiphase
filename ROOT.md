---
title: "Incompressible Two-Phase Flows -- Governing Equations"
author:
- Vincent Le Chenadec
- Stéphane Vincent
...

# Instantaneous equations

The following equations describe the dynamics of mixture of two ($k \in \left \llbracket 1, 2 \right \rrbracket$) immiscible and incompressible fluids. The equations are to be solved on an open bounded domain $\Omega \subset \mathbb{R} ^ D$. At any given instant $t > 0$, other relevant domains include the two open bounded domains occupied by each fluid, $\Omega_1 \left ( t \right )$ and $\Omega_2 \left ( t \right )$ respectively, as well as the interface
$$
\Gamma \left ( t \right ) = \overline{\Omega_1} \left ( t \right ) \cap \overline{\Omega_2} \left ( t \right )
$$
where $\overline{\cdot}$ denotes the closure operator.

## Indicator function

We define the indicator function
$$
\chi_k \left ( \mathbf{r}, t \right ) = \int_{\Omega_k \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} V \left ( \mathbf{r}' \right )
$$
where $\delta$ denotes the $D$-dimensional Dirac delta function.

### Rate of change

Reynolds transport theorem states that
$$
\frac{\partial \chi_k}{\partial t} \left ( \mathbf{r}, t \right ) = \int_{\Omega_k \left ( t \right )} \frac{\partial \delta}{\partial t} \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} V \left ( \mathbf{r}' \right ) + \int_{\partial \Omega_k \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathbf{w} \left ( \mathbf{r}', t \right ) \cdot \mathbf{n}_k \left ( \mathbf{r}' \right ) \mathrm{d} A \left ( \mathbf{r}' \right ).
$$

While the first term on the right-hand side vanishes, the second one remains and contains the interface velocity $\mathbf{w}$. Finally, usually the usual properties of the Dirac delta function this yields
$$
\frac{\partial \chi_k}{\partial t} \left ( \mathbf{r}, t \right ) = \mathbf{w} \left ( \mathbf{r}, t \right ) \cdot \mathbf{n}_k \left ( \mathbf{r}, t \right ) \int_{\partial \Omega_k \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} A \left ( \mathbf{r}' \right ).
$$
This notation is slightly abusive given that $\mathbf{w}$ and $\mathbf{n}_k$ are defined on $\partial \Omega_k$ only.

### Gradient

Taking the gradient of the characteristic function yields
$$
\begin{aligned}
\nabla_{\mathbf{r}} \chi_k \left ( \mathbf{r}, t \right ) & = \int_{\Omega_k \left ( t \right )} \nabla_{\mathbf{r}} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} V \left ( \mathbf{r}' \right ), \\
& = - \int_{\Omega_k \left ( t \right )} \nabla_{\mathbf{r}'} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} V \left ( \mathbf{r}' \right )
\end{aligned}
$$
and upon application of one of the many corollaries of the divergence theorem
$$
\nabla_\mathbf{r} \chi_k \left ( \mathbf{r}, t \right ) = - \int_{\partial \Omega_k \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathbf{n} \left ( \mathbf{r}' \right ) \mathrm{d} A \left ( \mathbf{r}' \right ).
$$
Finally, with the above-mentioned abuse of notation,
$$
\nabla_\mathbf{r} \chi_k \left ( \mathbf{r}, t \right ) = - \mathbf{n} \left ( \mathbf{r}, t \right ) \int_{\partial \Omega_k \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} A \left ( \mathbf{r}' \right ).
$$

### Putting it together

Comparing the two expressions (rate of change and gradient of the indicator function) we find
$$
\frac{\partial \chi_k}{\partial t} = - \mathbf{w} \cdot \nabla \chi_k,
$$
a transport equation move conventionally written
$$
\frac{\partial \chi_k}{\partial t} + \mathbf{w} \cdot \nabla \chi_k = 0.
$$

## Interface area

### Definition

The derivation of the characteristic function transport equation suggests the definition of a related quantity : the interface area
$$
a \left ( \mathbf{r}, t \right ) = \int_{\Gamma \left ( t \right )} \delta \left ( \mathbf{r}' - \mathbf{r} \right ) \mathrm{d} A \left ( \mathbf{r}' \right ).
$$

We note that
$$
\nabla \chi_k = - a \mathbf{n}_k.
$$

### Governing equation

One can show (it's a bit tedious but doable with tensor calculus)
$$
\frac{\partial a}{\partial t} + \nabla \cdot \left ( a \mathbf{w} \right ) = 2 a H \mathbf{w} \cdot \mathbf{n}
$$
where $H$ denotes the arithmetic average of the principal curvatures. $H$ and $\mathbf{n}$ are taken either with respect to fluid $1$ or fluid $2$. Given that on $\Gamma$,
$$
\left \{ \begin{aligned}
H_1 + H_2 & = 0, \\
\mathbf{n}_1 + \mathbf{n}_2 & = 0
\end{aligned} \right .
$$
the resulting equation does not change.

## Mass conservation

Main assumptions are non-reactive flows and massless interfaces.

### Bulk

The continuity equation reads
$$
\frac{\partial \rho_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \right ) = 0
$$
on $\Omega_k$.

It is usually more convenient to work with a form valid over the whole domain $\Omega$ (*one-fluid* form), which is typically achieved by multiplying by $\chi_k$
$$
\chi_k \left ( \frac{\partial \rho_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \right ) \right ) = 0.
$$

The following procedure will be repeated multiple times, so it will be detailed once here, and skipped later on
$$
\left ( \frac{\partial}{\partial t} \left ( \rho_k \chi_k \right ) + \nabla \cdot \left ( \rho_k \mathbf{u}_k \chi_k \right ) \right ) - \rho_k \left ( \frac{\partial \chi_k}{\partial t} + \mathbf{u}_k \cdot \nabla \chi_k \right ) = 0.
$$

Upon using the characteristic function equation, we find
$$
\frac{\partial}{\partial t} \left ( \rho_k \chi_k \right ) + \nabla \cdot \left ( \rho_k \chi_k \mathbf{u}_k \right ) = - \rho_k \left ( \mathbf{u}_k - \mathbf{w} \right ) \cdot \mathbf{n}_k a.
$$

The factor in front of $a$ in the right-hand side is commonly denoted $\dot{m}_k$ since it denotes the mass transferred between the two phases per unit time per unit area of interface. Hence,
$$
\frac{\partial}{\partial t} \left ( \rho_k \chi_k \right ) + \nabla \cdot \left ( \rho_k \mathbf{u}_k \chi_k \right ) = \dot{m}_k a
$$
where
$$
\dot{m}_k = - \rho_k \left ( \mathbf{u}_k - \mathbf{w} \right ) \cdot \mathbf{n}_k.
$$

### Interface

Finally, we note that per the Rankine-Hugoniot conditions (and for massless interfaces, *i.e.* without accumulation of surfactants for example)
$$
\dot{m}_1 + \dot{m}_2 = 0.
$$

At the interface, we define the velocity jump
$$
\left \llbracket u \right \rrbracket = - \sum_k \mathbf{u}_k \cdot \mathbf{n}_k = \sum_k \frac{\dot{m}_k}{\rho_k}.
$$

By realizing that
$$
\left \llbracket u \right \rrbracket = \dot{m}_1 \left ( \frac{1}{\rho_1} - \frac{1}{\rho_2} \right ) = \dot{m}_2 \left ( \frac{1}{\rho_2} - \frac{1}{\rho_1} \right ),
$$
we therefore note that the velocity is continuous

1. In the absence of mass transfers ($\dot{m}_1 = \dot{m}_2 = 0$),
1. With mass transfers between two phases of equal densities ($\rho_1 = \rho_2$).

### Volume conservation

For incompressible fluids, we finally note that
$$
\nabla \cdot \mathbf{u} = \left \llbracket u \right \rrbracket a
$$
where
$$
\mathbf{u} = \sum_k \mathbf{u}_k \chi_k.
$$

## Momentum conservation

Useful identity
$$
\left ( \mathbf{u} \cdot \nabla \right ) \mathbf{u} = \nabla \frac{\left \Vert \mathbf{u} \right \Vert ^ 2}{2} + \boldsymbol{\omega} \times \mathbf{u}
$$
where
$$
\boldsymbol{\omega} = \operatorname{curl} \mathbf{u}.
$$

### Bulk

On $\Omega_k$,
$$
\frac{\partial \rho \mathbf{u}_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \otimes \mathbf{u}_k \right ) = - \nabla p_k + \nabla \cdot \boldsymbol{\tau}_k + \rho_k \mathbf{g}
$$
where $p_k$ is the pressure and $\boldsymbol{\tau}_k$ the viscous stress tensor in fluid $k$.

By the same procedure as detailed in the case of the continuity equation, we find the *whole domain* formation
$$
\frac{\partial \rho_k \mathbf{u}_k \chi_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \otimes \mathbf{u}_k \chi_k \right ) = - \nabla \left ( p_k \chi_k \right ) + \nabla \cdot \left ( \boldsymbol{\tau}_k \chi_k \right ) + \rho_k \chi_k \mathbf{g} + \left ( \dot{m}_k \mathbf{u}_k - p_k \mathbf{n}_k + \boldsymbol{\tau}_k \cdot \mathbf{n}_k \right ) a.
$$

### Interface

For massless interfaces in isothermal flows, the Rankine - Hugoniot condition governing momentum transfers read
$$
\sum_k \left ( \dot{m}_k \mathbf{u}_k - p_k \mathbf{n}_k + \boldsymbol{\tau}_k \cdot \mathbf{n}_k \right ) = 2 \sigma H \mathbf{n}
$$
where $\sigma$ denotes the capillary tension.

## Kinetic energy

On $\Omega_k$,
$$
\mathbf{u}_k \cdot \left ( \frac{\partial \rho_k \mathbf{u}_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \otimes \mathbf{u}_k \right ) \right ) = \left ( \frac{\partial \rho_k e_k}{\partial t} + \nabla \cdot \left ( \rho_k e_k \mathbf{u}_k \right ) \right ) + e_k \left ( \frac{\partial \rho_k}{\partial t} + \nabla \cdot \left ( \rho_k \mathbf{u}_k \right ) \right )
$$
where
$$
e_k = \frac{\left \Vert \mathbf{u}_k \right \Vert ^ 2}{2}
$$
is the kinetic energy per unit mass.

