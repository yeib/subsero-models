# Yeib Models Hub 🧠🎙️🌐

Official open-weights distribution and release mirror for the **Yeib Ecosystem** desktop and mobile applications (including **SubSero**, **NeoTalker**, **PowerDesktop**, and related offline-first tools) developed by [Yeib](https://github.com/yeib).

---

## 📌 Purpose

This repository provides reliable, high-speed, direct CDN distribution of quantized speech-to-text (Whisper), neural machine translation (Bergamot NMT), and neural text-to-speech / voice synthesis models (Piper, ONNX TTS) utilized across the Yeib Ecosystem.

By distributing these models through versioned **GitHub Releases**, the Yeib Ecosystem ensures:
- **Universal Multi-App Hub**: A centralized, unified repository serving AI weights for audio transcription, language translation, and voice synthesis.
- **Resilience against link-rot**: Guaranteed availability regardless of third-party server deprecations, Hugging Face bandwidth throttles, or domain migrations.
- **Offline-First Privacy**: Once downloaded on demand by the user, all inference runs 100% locally on the device (via CPU SIMD/AVX2 or GPU acceleration) without sending telemetry, voice data, or text to external servers.
- **Ultra-lightweight Store Packages**: Applications (such as NeoTalker and SubSero) ship with minimal footprint out-of-the-box (e.g. lightweight built-in engines like SVOX Pico TTS), allowing users to selectively download higher-quality neural models on demand directly from this hub.
- **Zero Ingress/Egress Costs**: Free, uncapped, and high-throughput delivery for desktop and mobile users worldwide.

---

## 📦 Model Catalog

All model binaries are hosted directly in the [Releases Section](https://github.com/yeib/yeib-models/releases) of this repository.

### 1. Whisper Speech Recognition Models (GGML `q5_1`)
Optimized for local offline speech-to-text transcription via [`whisper.cpp`](https://github.com/ggerganov/whisper.cpp) (used in **SubSero** and **PowerDesktop**):

| Model File | Size | Memory Footprint | Recommended Use Case |
| :--- | :--- | :--- | :--- |
| `ggml-tiny-q5_1.bin` | ~31 MB | ~125 MB | Ultra-fast transcription, low-spec hardware, voice memos, and anime audio preview. |
| `ggml-base-q5_1.bin` | ~57 MB | ~210 MB | **Default & Recommended**. Optimal balance of speed and transcription accuracy. |
| `ggml-small-q5_1.bin` | ~181 MB | ~550 MB | Maximum accuracy for complex vocabulary, accented audio, and background noise. |

---

### 2. Neural Text-to-Speech Models (Piper ONNX / Modern Free TTS)
High-fidelity offline voice synthesis models optimized for **NeoTalker** (supplementing the ultra-compact default Pico TTS engine):

| Voice ID / Model | Language | Quality / Type | Size | Primary Assets |
| :--- | :--- | :--- | :--- | :--- |
| `es_ES-sharvard-medium` | Español (España) | Medium (High Naturalness) | ~60 MB | `es_ES-sharvard-medium.onnx`, `es_ES-sharvard-medium.onnx.json` |
| `es_MX-ald-medium` | Español (Latinoamérica / México) | Medium (Clean Dialogue) | ~62 MB | `es_MX-ald-medium.onnx`, `es_MX-ald-medium.onnx.json` |
| `en_US-lessac-medium` | English (US) | Medium (Balanced Narration) | ~63 MB | `en_US-lessac-medium.onnx`, `en_US-lessac-medium.onnx.json` |
| `en_US-ryan-medium` | English (US) | Medium (Deep Narrative) | ~63 MB | `en_US-ryan-medium.onnx`, `en_US-ryan-medium.onnx.json` |
| `en_GB-alba-medium` | English (UK) | Medium (Expressive) | ~61 MB | `en_GB-alba-medium.onnx`, `en_GB-alba-medium.onnx.json` |

---

### 3. Bergamot Neural Machine Translation Models (Marian NMT)
Compact, client-side neural translation models developed by the Bergamot Consortium and Mozilla Firefox Translations, quantized with **Intgemm 8-bit precision** for real-time CPU translation (used in **SubSero** and the Yeib translation pipeline).

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

Yeib apps implement automated multi-URL fallback mechanisms:

1. **Yeib Models Release Mirror (Primary CDN)**:
   - Base endpoint: `https://github.com/yeib/yeib-models/releases/download/{tag}/{filename}`
2. **Upstream Fallbacks**:
   - Whisper Models: Hugging Face mirror (`https://huggingface.co/ggerganov/whisper.cpp/resolve/main/{filename}`)
   - Bergamot Models: Mozilla Firefox Translations AWS S3 mirror
   - Neural TTS (Piper): Hugging Face Rhasspy / Piper voices distribution mirror

---

## ⚖️ Attribution & Licenses

All weights hosted or referenced in this repository are derived from open-source research and distributed under compliant licenses:

- **OpenAI Whisper**: [MIT License](https://github.com/openai/whisper/blob/main/LICENSE). Copyright © OpenAI.
- **whisper.cpp**: High-performance C/C++ port and GGML quantization by [Georgi Gerganov](https://github.com/ggerganov) under the [MIT License](https://github.com/ggerganov/whisper.cpp/blob/master/LICENSE).
- **The Bergamot Project**: Neural machine translation models developed by the University of Edinburgh, Charles University, University of Sheffield, University of Tartu, and Mozilla, licensed under [MPL-2.0](https://www.mozilla.org/en-US/MPL/2.0/) and [MIT](https://github.com/browsermt/students/blob/master/LICENSE).
- **Piper TTS / Rhasspy**: Fast local neural text-to-speech system developed by Michael Hansen, licensed under [MIT License](https://github.com/rhasspy/piper/blob/master/LICENSE.md). Voice models trained on open speech corpora (LibriTTS, Thorsten, Sharvard).
- **SVOX Pico TTS**: Open-source embedded speech synthesizer from the Android Open Source Project (AOSP), licensed under [Apache-2.0](http://www.apache.org/licenses/LICENSE-2.0).

---

## 🛡️ Repository Policy

Large binary weights are **never committed to the Git tree** to keep repository clones fast, clean, and lightweight. All binaries are attached exclusively as Release Assets.
