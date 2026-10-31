# SubSero Models Repository 🎙️🌐

Official open-weights distribution and release mirror for **SubSero**, the offline subtitle synchronization, transcription, and translation desktop application developed by [Yeib](https://github.com/yeib).

---

## 📌 Purpose

This repository provides reliable, high-speed, direct CDN distribution of quantized speech-to-text and neural machine translation (NMT) models utilized by SubSero. 

By distributing these models through versioned **GitHub Releases**, SubSero ensures:
- **Resilience against link-rot**: Guaranteed availability regardless of third-party server deprecations or domain migrations.
- **Offline-First Privacy**: Once downloaded by the user, all inference runs 100% locally on the device (via CPU SIMD/AVX2 or GPU acceleration) without sending telemetry or audio to the cloud.
- **Zero Ingress/Egress Costs**: Open and free delivery for SubSero desktop users.

---

## 📦 Model Catalog

All model binaries are hosted directly in the [Releases Section](https://github.com/yeib/subsero-models/releases) of this repository.

### 1. Whisper Speech Recognition Models (GGML `q5_1`)
Optimized for local inference via [`whisper.cpp`](https://github.com/ggerganov/whisper.cpp):

| Model File | Size | Memory Footprint | Recommended Use Case |
| :--- | :--- | :--- | :--- |
| `ggml-tiny-q5_1.bin` | ~31 MB | ~125 MB | Ultra-fast transcription, low-spec laptops, quick Japanese anime audio preview. |
| `ggml-base-q5_1.bin` | ~57 MB | ~210 MB | **Default & Recommended**. Optimal balance of speed, low latency, and transcription accuracy. |
| `ggml-small-q5_1.bin` | ~181 MB | ~550 MB | Maximum accuracy for complex vocabulary, noisy audio, and accented voices. |

### 2. Bergamot Neural Machine Translation Models
Compact Marian NMT models quantized via Intgemm for ultra-fast offline subtitle translation.
Asset naming schema: `{lang_id}-model.bin`, `{lang_id}-lex.s2t.bin`, `{lang_id}-vocab.spm`

- English ⇄ Spanish (`en-es`, `es-en`)
- English ⇄ French, German, Italian, Portuguese, Russian, Czech, and more.

---

## 🔗 Direct Download Endpoints

SubSero consumes model release assets using redundant fallback URLs:

- **Whisper Speech Models**:
  - **Primary**: `https://github.com/yeib/subsero-models/releases/download/v1.0.0/{filename}`
  - **Fallback (Hugging Face)**: `https://huggingface.co/ggerganov/whisper.cpp/resolve/main/{filename}`
- **Bergamot Translation Models**:
  - **Primary**: `https://github.com/yeib/subsero-models/releases/download/v1.0.0/{lang_id}-{filename}`
  - **Fallback (Mozilla S3)**: Original Bergamot S3 bucket mirrors

---

## ⚖️ Attribution & Licenses

The weights distributed in this repository are derived from open-source projects:

- **OpenAI Whisper**: Original speech recognition models released under the [MIT License](https://github.com/openai/whisper/blob/main/LICENSE). Copyright © OpenAI.
- **whisper.cpp**: GGML quantized distributions provided by [Georgi Gerganov](https://github.com/ggerganov) under the [MIT License](https://github.com/ggerganov/whisper.cpp/blob/master/LICENSE).
- **The Bergamot Project**: Local translation models developed by the University of Edinburgh, Charles University, University of Sheffield, University of Tartu, and Mozilla, licensed under [MPL-2.0](https://www.mozilla.org/en-US/MPL/2.0/) and [MIT](https://github.com/browsermt/students/blob/master/LICENSE).

---

## 🛡️ Repository Policy

Binary weights exceeding Git's standard file limits are **never committed to the git tree** to keep the repository clone size minimal. All binaries are attached exclusively as Release Assets.
