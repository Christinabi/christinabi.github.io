---
layout: default
mathjax: true
permalink: /governingEquation/
---

## Governing equations of lithium-ion battery model

### Governing equations

When we talked about the electrochemical model of a battery, five governing equations will be mentioned, those are [^1]

1. The solid phase mass conservation equation

$$
\frac{\partial c_s}{\partial t}=\frac{1}{r} \frac{\partial}{\partial r} \left( D_sr^2 \frac{\partial c_s}{\partial r}\right)
$$

2. The electrolyte phase mass conservation equation

$$
\frac{\partial \varepsilon_e c_e}{\partial t} = \nabla \cdot \left( D_{e,eff}\nabla c_e \right)+a_s\left(1-t_+^0\right)j
$$

3. The Solid phase charge conservation equation

$$
\nabla\cdot\left(\sigma_{eff}\nabla\phi_s\right)-a_sFj=0
$$

4. The electrolyte phase charge conservation equation

$$
\nabla\cdot\left(\kappa_{eff}\nabla\phi_e+\kappa_{D,eff}\nabla\ln c_e\right)+a_sFj=0
$$

5. Butler-Volmer kinetics relationship

$$
j=\frac{i_0}{F}\left\{\exp\left(\frac{\left(1-\alpha\right)F}{RT}\eta\right)-\exp\left(-\frac{\alpha F}{RT}\eta\right)\right\}
$$

### Mass conservation in solid

Inside a composite electrode, there are particles with various shapes and sizes. However, it is overwhelming if we are trying to model it. Therefore, we assume that spherical particles centered at grid location in the electrode, and that the concentration distribution within the particle is spherically symmetric. This way, we can model the concentration inside a particle using a radius dimension, which what we called a *pseudo-dimension*.  

Now let's look at the equation

$$
\frac{\partial c_s}{\partial t}=\frac{1}{r} \frac{\partial}{\partial r} \left( D_sr^2 \frac{\partial c_s}{\partial r}\right).
$$

The left-hand side describes how solid concentration changes over time. The right-hand side is actually the negative divergence of the concentration flux density

 $$
 \mathbf{N}=-D\nabla c,
 $$ 

where the minus sign shows that the flux density has the opposite direction to the gradient, implying that the ions move from a high concentration to a low concentration. Therefore the negative divergence represents net flux density into a particle, which is equal to the rate of change of lithium ion concentration in that particle. 

### Mass conservation in electrolyte

 We rewrite the equation

 $$
 \frac{\partial \varepsilon_e c_e}{\partial t} = \nabla \cdot \left( D_{e,eff}\nabla c_e \right)+a_s\left(1-t_+^0\right)j,
 $$

which has three terms. We notice we are familiar with the first two terms–the diffusion equation described by Fick's second law, which can be interpreted as the change of electrolyte concentration is partially due to the concentration gradient inside the electrolyte across the thickness. However, we've also noticed that different from inside the solid phase, where the ion concentration is only changed due to the gradient, ion concentration inside the electrolyte also changes when there is a flux coming from the solid particle (due to migration), hence the \\(a_s\left(1-t_+^0\right)j\\) term. But why \\(1-t_+^0\\) ? We recognize that \\(t_+^0\\) , called the transference number, is defined to be the fraction of current carried by the positively charged ion. Then \\(1-t_+^0\\)  is the fraction of lithium ions that stays in the electrolyte and contributes to change of concentration. 

### Charge conservation in solid

 We first take a look at a more general equation for a solid phase volume

 $$
 \nabla \cdot \mathbf{i_s} = \nabla \cdot \left(-\sigma\nabla\phi_s \right)=0.
 $$

Without the divergence term, we recognize that it's the Ohm's law, \\(\mathbf{i_s} = -\sigma\nabla\phi_s\\), where \\(\sigma\\) is the ionic conductivity. The negative sign is because here we take the gradient (\\(\nabla\\)) instead of the different (\\(\Delta\\)) of potential. This is also important that the left two terms equal to zero, which says that the same amount of charge must exit the volume as enters it. 

 So if we apply volume average theorem to \\(\nabla \cdot \left(-\sigma\nabla\phi_s \right)=0\\) we can get our target equation (without derivation)

 $$
 \nabla\cdot\left(\sigma_{eff}\nabla\phi_s\right)-a_sFj=0,
 $$

where the first term is the divergence of change of solid phase potential, while the second term is a correction term that represents the flux out of the surface inside of the solid particle.  Note that \\(a_s\\) is *specific interfacial surface area* of a particle, which is calculated as

$$
a_s = \frac{3\varepsilon_s}{R_s}.
$$

### Charge conservation in electrolyte

Essentially this equation describes by changing of electric potential, changing of chemical potential in the electrolyte, and a correction term comes from the interface as

$$
\nabla\cdot\left(\kappa_{eff}\nabla\phi_e+\kappa_{D,eff}\nabla\ln c_e\right)+a_sFj=0
$$

So far, we have seen similar terms as the first and the third term. However, the second term is not obvious: where the \\(\ln c\\) comes from? This is because in the literature, the chemical potential gradient is usually expressed in terms of \\(\nabla\ln c\\) via

$$
\nabla \mu_e =\frac{\partial \mu_e}{\partial \ln c}\nabla\ln c.
$$

Also note that the sign in front of \\(a_s Fj\\) is positive, which is opposite to that from the solid phase equation. This is because now we are considering the surface outside the solid/electrolyte interface that has the same direction as the ion flux.

### Butler-Volmer kinetics equation

Kinetics describes "how fast" reactions take place, in this case, how quickly lithium ions move across the solid/electrolyte interface, using the Butler-Volmer equation

$$
j=\frac{i_0}{F}\left\{\exp\left(\frac{\left(1-\alpha\right)F}{RT}\eta\right)-\exp\left(-\frac{\alpha F}{RT}\eta\right)\right\}
$$

Specifically, there are two terms inside the bracket, which describes the reduction reaction and oxidation reaction, respective. \\(\eta\\) is the overpotential

$$
\eta = \left(\phi_s-\phi_e\right)-U_{OCV}
$$

which indicates the direction of lithium ion flux by comparing the potential difference between solid and electrolyte with the open-circuit voltage, \\(U_{OCV}\\).

Hopefully by now you've had an intuitive understanding of all five of the governing equations. These equations are powerful enough to describe lithium-ion batteries with various electrode materials. I will see you next time!


 [^1]: This post is inspired by Prof. Plett's book on battery modeling: Plett, Gregory L. Battery management systems, Volume I: Battery modeling. Vol. 1. Artech House, 2015.
