# lt_models

Model assets for [secure-transcript](https://github.com/diegoje/secure-transcript).

## What's here

### Re-hosted (this repo)
- **`pyannote-community-1.zip`** — Pyannote speaker-diarization pipeline
  (Hervé Bredin et al., MIT licensed). Includes pre-exported ONNX files
  for GPU acceleration via ONNX Runtime. Re-hosted because the upstream
  Hugging Face model is gated (requires account + license agreement +
  token), which breaks the standalone-installer UX.
- **`all-MiniLM-L6-v2.zip`** — sentence-transformers/all-MiniLM-L6-v2
  embedding model (Apache 2.0). Used by Phase 7 (Library semantic
  search + cross-meeting RAG). Bundled here as a corp-firewall-friendly
  fallback to the in-MSI copy — Hugging Face is sometimes blocked on
  enterprise networks; GitHub usually isn't.
  Contents: `model.onnx` (FP32, ~87 MB) + tokenizer files
  (`tokenizer.json`, `tokenizer_config.json`, `config.json`,
  `special_tokens_map.json`, `vocab.txt`). Total zipped: ~83 MB.

### Pulled directly from Hugging Face (not re-hosted)
- Whisper GGML weights → `huggingface.co/ggerganov/whisper.cpp`
- Gemma 4 E2B IT Q8 GGUF → `huggingface.co/ggml-org/gemma-4-E2B-it-GGUF`

Both are public and HF is a reliable CDN; re-hosting would be redundant.

## Manifest

The app reads `MANIFEST.json` (in each release) to discover what's
available + verify SHA256 integrity before loading.
