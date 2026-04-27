# Autoregressive Language Modeling for Speech Packet Loss Concealment in Neural Codec Domain

**Carlo Aironi, Leonardo Gabrielli, Samuele Cornell, Stefano Squartini**  
Università Politecnica delle Marche, Italy · Carnegie Mellon University, USA
>
> **This repository is under active development.** Code and pretrained models will be released upon paper acceptance.

## Method Overview

PLCLM frames PLC as a **causal next-token prediction** problem on discrete codeword sequences produced by the [Descript Audio Codec (DAC)](https://github.com/descriptinc/descript-audio-codec). A decoder-only **RoFormer** Transformer is trained to predict missing codewords from past context only, ensuring strict causality and an algorithmic latency of **11.6 ms**.

Key design choices:

- **Codec-domain operation** - PLC is performed before decoding, avoiding the overhead of decoding and re-encoding that waveform-based approaches entail.
- **Codebook selection** - A redundancy analysis shows that 4 of the 9 DAC codebooks suffice for perceptually adequate speech reconstruction, reducing computational cost.
- **Weighted loss** - A hierarchical cross-entropy loss prioritizes lower-index codebooks, which encode the most perceptually salient features.
- **PLCLM+ATT variant** - An optional causal cross-codebook attention mechanism exploits inter-codebook dependencies while respecting the RVQ hierarchy.

Audio examples comparing clean, corrupted and PLCLM-restored speech across packet loss rates from 10% to 60% are available on the [Demo page 🔊](https://aircarlo.github.io/PLCLM/):

## Contact

**Carlo Aironi** - [c.aironi@staff.univpm.it](mailto:c.aironi@staff.univpm.it)  
Department of Information Engineering, Università Politecnica delle Marche, Ancona, Italy
