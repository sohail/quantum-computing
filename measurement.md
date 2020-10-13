# Measurement Postulate

A central principle of qunatum mechanics is that measurement outcomes are probabilistic.
A Qubit in state **PSI(Ψ)** is in a super position of states... **|Ψ⟩ = &prop;|0&rang; + &Beta;|1&rang;**

The following expression means that the inner product after it gets normalized would result in state **|1&rang;**(up spin).
**&vert;&lang;1|&phi;&rang;&vert;&sup2;|1&rang;**

The following expression means that the inner product after it gets normalized would result in state **|0&rang;**(down spin).
**&vert;&lang;0|&phi;&rang;&vert;&sup2;|0&rang;**

Then, the following expression generalizes this process of getting the probability of bit string **x&#8321;...x&#8345;** after the inner product between **x&#8321;...x&#8345;** and **n** qubit based joint state(system of qubits) gets normalized.  
**&vert;&lang;x&#8321;...x&#8345;|&phi;&#8321;...&phi;&#8345;&rang;&vert;&sup2;|x&#8321;...x&#8345;&rang;**

## Subsystem measurement
Now in the following two cases of measurement, we are measuring the first qubit in a joint state of system of 3 qubits and we are measuring in such a way that other two qubits remain undisturbed...

**&vert;&lang;0x&#8321;x&#8322;|&phi;&rang;&vert;&sup2;|0&#8321;x&#8322;&rang;**
where (x&#8321;,x&#8322;) &#8712; (0,1) 

**&vert;&lang;1x&#8321;x&#8322;|&phi;&rang;&vert;&sup2;|1x&#8321;x&#8322;&rang;**
where (x&#8321;,x&#8322;) &#8712; (0,1)
 
Similarly we can compute the effect of subsystem measurement on any nqubit state.

## Subsystem measurement and entangled states
Lets apply the same paradigm that we discussed so far to understand entangled states...
**|Ψ⟩ = 1/&#8730;2|0&rang; +  1/&#8730;2|1&rang;**
here the state PSI(Ψ) is a system of three qubits and these qubits are entangled. The above equation tells us that there's 50 50 chance of all qubits being 0 or all qubits being 1. Moving forward, and it is the outcome of the measurement outcome of very first qubit which will determine outcomes of the other two qubits of this joint state. Lets now go ahead and put the outcome of entangled PSI(Ψ) state in bra-ket notation...

**&vert;&lang;0x&#8322;x&#8323;|&phi;&rang;&vert;&sup2;|000&rang;**
where x&#8322;x&#8323; = 00

**&vert;&lang;1x&#8322;x&#8323;|&phi;&rang;&vert;&sup2;|111&rang;**
where x&#8322;x&#8323; = 11

It is the entanglement which makes it possible to create a complete **2&#8319;** dimensional complex vector space to do our computation in using just **n** physical qubits. In the next couple of papers we'll cover that topic.