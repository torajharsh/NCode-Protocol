# NCode Protocol Specification v0.1

**Status:** Pre-Alpha / RFC <br>
**Author:** Raj Harsh

## 1. Architectural Philosophy
NCode treats video as a **Distributed Inference Task**. It assumes the Receiver is a latent-space engine capable of reconstructing visual reality from "learned weights" and "activation vectors."

## 2. The Semantic Layered Model
### 2.1 The Asset Plane (Persistence)
Instead of pixels, the backend identifies recurring entities (Actors, Environments, Objects). These are assigned a **Global Reference ID**. If a scene returns to a cached asset, the protocol reuses the weights, streaming only the new perspective deltas.

### 2.2 The Weight Plane (Modular Fragments)
Weights are delivered in temporal "Context Windows" (e.g., 600 seconds). This **JIT Swapping** ensures high-fidelity without exceeding device VRAM limits.

### 2.3 The Latent Plane (The Interaction Stream)
Transmits $N$-dimensional tensors representing "Intent" (Camera Path, Lighting, Movement).

## 3. Implicit Neural Storage (INS)
The backend stores a "Universal Base Model" and "Content LoRAs" instead of MP4 files. This achieves extreme storage efficiency and enables on-the-fly "Neural Transcoding" for specific user hardware.

## 4. Mathematical Foundation (RFC / TODO)
Currently seeking help with mathematical research and formalization for:
* **TODO [Math-01]:** Latent Delta ($\Delta z$) Entropy Optimization. <br> *Require a robust formula for minimizing the tensor size while maintaining high-fidelity reconstruction on the NPU manifold.*
* **TODO [Math-02]:** Semantic Checksum Thresholds ($\epsilon$) for drift detection. <br> *Research into "Perceptual Loss Hashes" that can detect identity drift without the computational overhead of traditional VGG or LPIPS metrics.*
* **TODO [Math-03]:** Cross-architecture Quantization Determinism. <br> *Standardize floating-point precision across varying hardware architectures (NVIDIA TensorRT vs. Apple CoreML) to ensure bit-identical reconstruction.*

## 5. Audio Handling
Audio is transmitted via traditional high-fidelity bitstreams (Opus/AAC) to maintain 1:1 auditory accuracy, remaining outside the neural reconstruction loop as for now. We might eventually expand into the territory of audio, with possibilities for specific definition models and adapters, such as identity, expression, emotion, mood, tone and other parameters.
