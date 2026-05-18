| Variable                  | Superconducting Noise Model                                                            | Neutral-Atom Noise Model                                                                                                                                          |
| ------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| noise (Generation Params) | `p_depol1`: 0.001<br>`p_depol2`: 0.005<br>`p_meas`: 0.005<br>`p_reset`: 0.001          | `p_depol1`: 0.001<br>`p_depol2`: 0.005<br>`p_meas`: 0.005<br>`p_reset`: 0.001<br>`p_erasure`: 0.002<br>`erasure_depol_strength`: 0.75<br>`p_correlated_zz`: 0.001 |
| mean_herald_rate          | 0.0 (or completely absent). Superconducting hardware cannot herald errors mid-circuit. | 0.0019. The hardware explicitly flags a small percentage of errors as atom loss.                                                                                  |
| mean_detector_rate        | ~0.045. Detectors only fire based on random Pauli noise.                               | 0.054. Detectors fire slightly more often because atom loss injects strong depolarizing noise.                                                                    |


1. "p_erasure": 0.002

What it means: There is a 0.2% probability that an atom is "lost" or erased during a single two-qubit gate.

Neutral atoms are held in place by focused laser beams called optical tweezers. Occasionally, an atom might be knocked out of its tweezer by a background gas collision, or the laser might accidentally excite the atom into a "dark state" outside the computational $0$ and $1$ basis.

https://www.quera.com/glossary/optical-tweezers
https://quantumzeitgeist.com/neutral-atom-processors-demonstrate-resilience-through-atom-replacement-and-coherence-say-microsoft-and-atom-computing/

2. "erasure_depol_strength": 0.75

What it means: When an atom is erased, it is completely scrambled, represented by a 75% chance of applying a random Pauli error ($X$, $Y$, or $Z$).

If an atom is lost, you effectively have no information about its quantum state. In quantum mechanics, a state with zero information is called "maximally mixed.".

https://learn.microsoft.com/en-us/azure/quantum/overview-qdk-neutral-atom-simulator

3. "p_correlated_zz": 0.001

What it means: There is a 0.1% probability that a two-qubit gate fails by applying a phase flip ($Z$ error) to both interacting qubits at the exact same time.

Neutral-atom quantum computers perform two-qubit gates (like a CZ gate) by exciting both atoms to a highly energetic "Rydberg state.". They rely on the Rydberg blockade, where atoms are close enough that they prevent each other from both reaching this state. If the laser pulses are slightly mistimed or the atoms shift slightly, the gate fails symmetrically, leaving a phase error on both atoms.

https://journals.aps.org/prxquantum/abstract/10.1103/PRXQuantum.4.020336?ft=1