# SubSero Models Repository 🎙️🌐

Official open-weights distribution and release mirror for **SubSero**, the offline subtitle synchronization, speech recognition, and translation desktop application developed by [Yeib](https://github.com/yeib).

---

## 📌 Purpose

This repository provides reliable, high-speed, direct CDN distribution of quantized speech-to-text (Whisper) and neural machine translation (Bergamot NMT) models utilized by SubSero.

By distributing these models through versioned **GitHub Releases**, SubSero ensures:
- **Resilience against link-rot**: Guaranteed availability regardless of third-party server deprecations or domain migrations.
- **Offline-First Privacy**: Once downloaded by the user, all inference runs 100% locally on the device (via CPU SIMD/AVX2 or GPU acceleration) without sending telemetry or audio to the cloud.
- **Zero Ingress/Egress Costs**: Free, uncapped, and high-throughput delivery for SubSero desktop users.

---

## 📦 Model Catalog

All model binaries are hosted directly in the [Releases Section](https://github.com/yeib/subsero-models/releases) of this repository.

### 1. Whisper Speech Recognition Models (GGML `q5_1`)
Optimized for local offline inference via [`whisper.cpp`](https://github.com/ggerganov/whisper.cpp):

| Model File | Size | Memory Footprint | Recommended Use Case |
| :--- | :--- | :--- | :--- |
| `ggml-tiny-q5_1.bin` | ~31 MB | ~125 MB | Ultra-fast transcription, low-spec hardware, anime audio preview. |
| `ggml-base-q5_1.bin` | ~57 MB | ~210 MB | **Default & Recommended**. Optimal balance of speed and transcription accuracy. |
| `ggml-small-q5_1.bin` | ~181 MB | ~550 MB | Maximum accuracy for complex vocabulary, accented audio, and background noise. |

---

### 2. Bergamot Neural Machine Translation Models (Marian NMT)
Compact, client-side neural translation models developed by the Bergamot Consortium and Mozilla Firefox Translations, quantized with **Intgemm 8-bit precision** for real-time CPU translation.

Each language model consists of 3 dedicated component files:
- `{id}-model.bin`: Intgemm 8-bit Marian neural network weights.
- `{id}-lex.s2t.bin`: Shortlist lexical translation probability table.
- `{id}-vocab.spm`: SentencePiece subword vocabulary tokenizer.

#### Supported Language Pairs (18 Models):

| Pair ID | Source Language | Target Language | Total Size | Primary Assets |
| :--- | :--- | :--- | :--- | :--- |
| **`en-es`** | Inglés (English) | **Español (Spanish)** | ~20.3 MB | `en-es-model.bin`, `en-es-lex.s2t.bin`, `en-es-vocab.spm` |
| **`es-en`** | **Español (Spanish)** | Inglés (English) | ~20.8 MB | `es-en-model.bin`, `es-en-lex.s2t.bin`, `es-en-vocab.spm` |
| `en-fr` | Inglés (English) | Francés (French) | ~24.7 MB | `en-fr-model.bin`, `en-fr-lex.s2t.bin`, `en-fr-vocab.spm` |
| `fr-en` | Francés (French) | Inglés (English) | ~25.5 MB | `fr-en-model.bin`, `fr-en-lex.s2t.bin`, `fr-en-vocab.spm` |
| `en-de` | Inglés (English) | Alemán (German) | ~20.9 MB | `en-de-model.bin`, `en-de-lex.s2t.bin`, `en-de-vocab.spm` |
| `de-en` | Alemán (German) | Inglés (English) | ~21.9 MB | `de-en-model.bin`, `de-en-lex.s2t.bin`, `de-en-vocab.spm` |
| `en-it` | Inglés (English) | Italiano (Italian) | ~21.4 MB | `en-it-model.bin`, `en-it-lex.s2t.bin`, `en-it-vocab.spm` |
| `it-en` | Italiano (Italian) | Inglés (English) | ~22.1 MB | `it-en-model.bin`, `it-en-lex.s2t.bin`, `it-en-vocab.spm` |
| `en-pt` | Inglés (English) | Portugués (Portuguese) | ~21.4 MB | `en-pt-model.bin`, `en-pt-lex.s2t.bin`, `en-pt-vocab.spm` |
| `pt-en` | Portugués (Portuguese) | Inglés (English) | ~21.9 MB | `pt-en-model.bin`, `pt-en-lex.s2t.bin`, `pt-en-vocab.spm` |
| `en-ru` | Inglés (English) | Ruso (Russian) | ~20.1 MB | `en-ru-model.bin`, `en-ru-lex.s2t.bin`, `en-ru-vocab.spm` |
| `ru-en` | Ruso (Russian) | Inglés (English) | ~22.1 MB | `ru-en-model.bin`, `ru-en-lex.s2t.bin`, `ru-en-vocab.spm` |
| `en-cs` | Inglés (English) | Checo (Czech) | ~20.5 MB | `en-cs-model.bin`, `en-cs-lex.s2t.bin`, `en-cs-vocab.spm` |
| `cs-en` | Checo (Czech) | Inglés (English) | ~21.4 MB | `cs-en-model.bin`, `cs-en-lex.s2t.bin`, `cs-en-vocab.spm` |
| `en-et` | Inglés (English) | Estonio (Estonian) | ~19.7 MB | `en-et-model.bin`, `en-et-lex.s2t.bin`, `en-et-vocab.spm` |
| `et-en` | Estonio (Estonian) | Inglés (English) | ~20.9 MB | `et-en-model.bin`, `et-en-lex.s2t.bin`, `et-en-vocab.spm` |
| `en-bg` | Inglés (English) | Búlgaro (Bulgarian) | ~22.6 MB | `en-bg-model.bin`, `en-bg-lex.s2t.bin`, `en-bg-vocab.spm` |
| `bg-en` | Búlgaro (Bulgarian) | Inglés (English) | ~23.1 MB | `bg-en-model.bin`, `bg-en-lex.s2t.bin`, `bg-en-vocab.spm` |

---

## 🔗 Direct Download Endpoints & Redundancy

SubSero implements an intelligent multi-URL fallback mechanism:

1. **Whisper Speech Models**:
   - **Primary**: `https://github.com/yeib/subsero-models/releases/download/v1.0.0/{filename}`
   - **Fallback (Hugging Face)**: `https://huggingface.co/ggerganov/whisper.cpp/resolve/main/{filename}`
2. **Bergamot Translation Models**:
   - **Primary**: `https://github.com/yeib/subsero-models/releases/download/v1.0.0/{id}-{filename}`
   - **Fallback (Mozilla AWS S3)**: Upstream Marian models mirror

---

## ⚖️ Attribution & Licenses

All weights in this repository are derived from open-source research and distributed under compliant licenses:

- **OpenAI Whisper**: [MIT License](https://github.com/openai/whisper/blob/main/LICENSE). Copyright © OpenAI.
- **whisper.cpp**: High-performance C/C++ port and GGML quantization by [Georgi Gerganov](https://github.com/ggerganov) under the [MIT License](https://github.com/ggerganov/whisper.cpp/blob/master/LICENSE).
- **The Bergamot Project**: Neural machine translation models developed by the University of Edinburgh, Charles University, University of Sheffield, University of Tartu, and Mozilla, licensed under [MPL-2.0](https://www.mozilla.org/en-US/MPL/2.0/) and [MIT](https://github.com/browsermt/students/blob/master/LICENSE).

---

## 🛡️ Repository Policy

Large binary weights are **never committed to the Git tree** to keep repository clones fast and lightweight. All binaries are attached exclusively as Release Assets.
