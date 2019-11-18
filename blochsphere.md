# State of Qubit in Blochsphere
---

__In xy plane__(the superposition of states)...


**|Ψ⟩ = &prop;|0&rang; + &Beta;|1&rang;**

where...

> **&prop;, &Beta; &isin; &complexes;** 
> |**&prop;**|&sup2; + |**&Beta;**|&sup2; = **1**

```
A qubit is a quantum particle and it is a probability wave as well. We are interested in a position of qubit. Position of a qubit is a real world property and it is either 0 or 1. 
Through interference we assign probabilities in the form of amplitudes to the different states of a qubit in a superposition of states.

These amplitudes live in a complex space and, we are interested in the likelihood of either 0 or 1. Put differently, we are interested in the probability distribution of superposition of states and for that, we ensure that absolute square of each of the amplitudes when added together give 1.      
```

__In polar plane__(the superposition of states)...

|&Psi;&rang; = **r&#x2080;exp(&ImaginaryI;&Phi;&#x2080;)|0&rang; + r&#x2081;exp(&ImaginaryI;&Phi;&#x2081;)|1&rang;**

where...

> **r** is the magnitude, the length of hypotenuse

> **&Phi;** is the angle between between lines representing hypotenuse and adjacent

|&Psi;&rang; = **exp(&ImaginaryI;&Phi;&#x2080;)[r&#x2080;|0&rang; + r&#x2081;exp(&ImaginaryI;(&Phi;&#x2081; - &Phi;&#x2080;))|1&rang;**]

|&Psi;&rang; = **r&#x2080;|0&rang; + r&#x2081;exp(&ImaginaryI;&Phi;)|1&rang;**

> dropped **exp(&ImaginaryI;&Phi;&#x2080;)** out of consideration because during measurements it'll not make any difference

__In Blochsphere space__(the superposition of states)...

**|&Psi;&rang; = cos(&theta;)/2 + exp(&ImaginaryI;&Phi;)sin(&theta;)/2**
 
where...

 > **0 &lt; &theta; &lt;= &pi;**

 > **0 &lt; &Phi; &lt;= 2&pi;**


### So how does we arrive from the 2D **xy plane** to the **polar plane** and then into the 3D **Blochsphere plane**...

Qubit's superposition of states is represented by two complex numbers, **&prop;**, **&Beta;** in xy plane. In polar plane 4 real parameters  **r**&#x2080;, **r**&#x2081;, **&Phi;**&#x2080; and  **&Phi;**&#x2081; are needed to describe the same state. We droped the **exp(&ImaginaryI;&Phi;&#x2080;)** due to it being irrelevant in the final measurements. Now we are left with three of them **r**&#x2080;, **r**&#x2081; and (**&Phi;**&#x2081; - **&Phi;**&#x2080;).
 **r**&#x2080;, **r**&#x2081; are non-negtive real numbers, both have to satisfy the normalization constraint of (**r**&#x2080;&sup2; + **r**&#x2081;&sup2; = **1**) and hence **r**&#x2080;, **r**&#x2081; can just be replaced with two trignometric ratios the **cos(&theta;)** and the **sin(&theta;)** because (**cos(&theta;)**&sup2; + **sin(&theta;)**&sup2; = **1**&sup2;). That is how we can come to the conclusion that whole state of Qubit in Blochsphere can be described with just two parameters **&theta;** and **&Phi;**.  

``` 

Further readings and references

```
* [Spin-1/2 particle](https://en.wikipedia.org/wiki/Spin-%C2%BD)
* [Planck's constant](https://en.wikipedia.org/wiki/Planck_constant)
* [A great lecture video on Blocksphere](https://www.youtube.com/watch?v=vUVkS1XZVCc)
* [Great site for Blochsphere simulation](https://www.st-andrews.ac.uk/physics/quvis/simulations_html5/sims/blochsphere/blochsphere.html)

