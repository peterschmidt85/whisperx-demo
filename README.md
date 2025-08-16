# WhisperX

Run [WhisperX](https://github.com/m-bain/whisperX) speech recognition on any cloud or on-prem GPU via [dstack](https://github.com/dstackai/dstack/).

**Prerequisites:** Install dstack ([installation guide](https://dstack.ai/docs/installation/))

## Quick Start

```bash
git clone https://github.com/peterschmidt85/whisperx-demo
cd whisperx-demo
dstack init
dstack apply -f .dstack.yml \
    -e AUDIO_URL="https://example.com/audio.wav"
```

## Configuration

**Required:**
- `AUDIO_URL`: Audio file URL or path

**Optional:**
- `LANGUAGE`: Language code (e.g., "en", "es", "fr")
- `MODEL`: WhisperX model ("large-v2", "medium", "small")
- `MIN_SPEAKERS`/`MAX_SPEAKERS`: Speaker diarization limits
- `HF_TOKEN`: Hugging Face token for gated models
- `OUTPUT_FORMAT`: Output formats (default: "srt,txt,json")

## GPU & Spot Instances

Use GPU acceleration:
```bash
dstack apply -f .dstack.yml --gpu 24GB \
    -e AUDIO_URL="https://example.com/audio.wav"
```

Use spot instances for cost savings:
```bash
dstack apply -f .dstack.yml --spot \
    -e AUDIO_URL="https://example.com/audio.wav"
```

Combine GPU and spot instances:
```bash
dstack apply -f .dstack.yml --gpu 24GB --spot \
    -e AUDIO_URL="https://example.com/audio.wav"
```

GPU patterns: `1`, `24GB`, `24GB..40GB`, `H100:2`

**More info:** [dstack Documentation](https://dstack.ai/docs/)
