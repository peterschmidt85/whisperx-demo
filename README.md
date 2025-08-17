# WhisperX

Run [WhisperX](https://github.com/m-bain/whisperX) speech recognition on any cloud or on-prem GPU via [dstack](https://github.com/dstackai/dstack/).

**Prerequisites:** Install dstack ([installation guide](https://dstack.ai/docs/installation/))

## Quick Start

```bash
git clone https://github.com/peterschmidt85/whisperx-demo
cd whisperx-demo
dstack init
dstack apply -f fleet.dstack.yml  # Create fleet
dstack apply -f .dstack.yml \
    -e AUDIO_URL="https://example.com/audio.wav"
```

The task uploads transcription results and provides download links. You can also access logs later with:
```bash
dstack logs whisperx-demo
```

## Configuration

**Required:**
- `AUDIO_URL`: Audio file URL or path

**Optional:**
- `LANGUAGE`: Language code (e.g., "en", "es", "fr")
- `MODEL`: WhisperX model ("large-v2", "medium", "small")
- `MIN_SPEAKERS`/`MAX_SPEAKERS`: Speaker diarization limits
- `HF_TOKEN`: Hugging Face token for gated models
- `DIARIZE`: Enable speaker diarization (default: true)
- `HIGHLIGHT_WORDS`: Enable word-level highlighting

## Output

The task saves transcription results to `./output` directory and uploads them via download links instead of printing to stdout.

**More info:** [dstack Documentation](https://dstack.ai/docs/)
