AlphaQubit's Original Scope (Superconducting)

The 2024 AlphaQubit model was built to solve the problems specific to Google's own superconducting processor, Sycamore.

The Training Data: It was pre-trained on simulated depolarizing noise and fine-tuned on tens of millions of actual hardware samples from Sycamore.

Hardware-Specific Features: It utilized superconducting-specific telemetry, such as "soft readouts" (using the raw analog probability of a measurement rather than a strict 0 or 1) and specific microwave cross-talk signatures.

Because it was built by the team building superconducting chips, it ignored heralded atom loss and Rydberg blockades, because those simply don't exist in Sycamore.