# QcHack_Qutech
1) Create python venv
2) `pip3 install -e "git+https://github.com/QuTech-Delft/qne-adk.git@a125b2d27f1e5fef2822329cf824b18e22e9d00e#egg=qne-adk"`<br>
`pip3 install squidasm==0.8.4 --extra-index-url https://pypi.netsquid.org`<br>
3) `qne application create qkd alice bob`

1)making entangled bell state
The source centre chooses the EPR pair(Entangled Bell State) |φ+⟩=(1/√2)(|00⟩+|11⟩), sends the first particle |φ+⟩₁ to Alice and second particle |φ+⟩₂ to Bob.

2)
Alice makes a measurement with a direction randomly chosen between {0, π/8 , π/4}, whereas Bob makes a measurement with a direction randomly chosen between {−π/8 , 0, π/8}. They record the measurement result and broadcast the measurement basis which they used, through the classical channel.

3)
Thus, Alice and Bob now know each other's choice. They divide the measurement result into two groups: one is the decoy qubits G₁ where they choose different measurement basis and another is the raw key qubits G₂ where they choose the same measurement basis.

4)
The group G₁ is used to detect whether there is an eavesdropping. To detect eavesdropping, they can compute the test statistic S using the correlation coefficients between Alice’s bases and Bob’s, similar to that shown in the Bell test experiments. If there is an error in the value of S, which means that there is also a eavesdropper, Alice and Bob will conclude that the quantum channel is not safe and they will interrupt this communication and start a new one.

5)
If the quantum channel is safe, G₂ can be used as the raw keys because Alice and Bob can receive the same measurements. Both Alice and Bob agree on that the measurement |0⟩ represents the classical bit 0, while the measurement |1⟩ represents the classical bit 1, and thus get their key string.
