# QcHack_Qutech
1) Create python venv
2) `pip3 install -e "git+https://github.com/QuTech-Delft/qne-adk.git@a125b2d27f1e5fef2822329cf824b18e22e9d00e#egg=qne-adk"`<br>
`pip3 install squidasm==0.8.4 --extra-index-url https://pypi.netsquid.org`<br>
3) `qne application create qkd alice bob`

**Part 1**

For Part 1 of the challenge, we have implemented E91 protocol. Below is the summary of how the protocol works.

1) Making entangled bell state
The source centre chooses the EPR pair(Entangled Bell State) |φ+⟩=(1/√2)(|00⟩+|11⟩), sends the first particle |φ+⟩₁ to Alice and second particle |φ+⟩₂ to Bob.

2) Alice makes a measurement with a direction randomly chosen between {0, π/8 , π/4}, whereas Bob makes a measurement with a direction randomly chosen between {−π/8 , 0, π/8}. They record the measurement result and broadcast the measurement basis which they used, through the classical channel.

3) Thus, Alice and Bob now know each other's choice. They divide the measurement result into two groups: one is the decoy qubits G₁ where they choose different measurement basis and another is the raw key qubits G₂ where they choose the same measurement basis.

4) The group G₁ is used to detect whether there is an eavesdropping. To detect eavesdropping, they can compute the test statistic S using the correlation coefficients between Alice’s bases and Bob’s, similar to that shown in the Bell test experiments. If there is an error in the value of S, which means that there is also a eavesdropper, Alice and Bob will conclude that the quantum channel is not safe and they will interrupt this communication and start a new one.

5) If the quantum channel is safe, G₂ can be used as the raw keys because Alice and Bob can receive the same measurements. Both Alice and Bob agree on that the measurement |0⟩ represents the classical bit 0, while the measurement |1⟩ represents the classical bit 1, and thus get their key string.

**Part 2**
 
Noise is inherent part of the current NISQ hardware. Our idea is to implement the protocol with for error correction. Surface code is a 2D error correcting code that can error correct both bit-flip and phase-flip errors and it is quite robust. It has the advantage that the size of the surface code can be varied based on the availability of number of physical qubits, thus can make use of available qubits to the maximum extent. Finding simulator results by extending our implementation of E91 protocol with surface code can be promising to work with NISQ computers.


**Open Question**

For open question, we believe extending the procedure of the paper by [Mario Mastani](https://www.researchgate.net/publication/337901106_Non-ambiguity_quantum_teleportation_protocol) on Non-ambiguity teleportation protocol for entanglement pair generation and communication can lead to a better protocol with no or very minimal classical communication required.
