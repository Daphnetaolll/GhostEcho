# GhostEcho 
## Live Interactive Web Audio FX - Memory Distortion Audio Tool 

**Developer:** Daphne Tao - *DAPHNIII*

GhostEcho is a browser-based audio tool that transforms sound into expressive, memory-like distortions.
It is designed for musicians, live performers, and even non-DAW users who want to explore sound design in an intuitive and creative way.

Inspired by the way melodies replay and warp inside human memory, GhostEcho allows users to shape tracks, voices, and instruments into evolving textures that feel nostalgic, blurred, and ghostly.

**GhostEcho supports two workflows:**

- **Studio Mode:** apply effects to full tracks
- **Live Mode:** process microphone or instrument input in real time

## Introduction

GhostEcho is built as a hybrid audio system combining:

- Python + Gradio for the interactive web interface
- Csound as the DSP engine for all real-time effect processing
- Wavesurfer.js for waveform visualization
- Custom-designed algorithms inspired by memory distortion and decayed reflections

The goal is to create a sound tool that is both artist-friendly and technically expressive, enabling users to perform, experiment, and reshape audio instantly without needing a DAW.

## Features
### Studio Mode
Upload a WAV/MP3, apply effects, preview instantly, and download high-quality audio.

Includes:

- Modes: Echo / Memory / Lo-fi / Ghost / Slow Fade
- Intensity Knob: mapped to multiple parameters
- Fast Preview for quick listening
- High-Quality Render for exporting final audio
- Waveform Visualization 

Output formats:

- WAV 
- MP3 

### Live Mode — Real-Time Performance Effects

Use a microphone, guitar, modular synth, or any instrument as input and perform with expressive, interactive effects.

**Live Effects:**

- **Pitch Shifter:** Dry/Wet control, Semitone shifting

- **Ring Modulation:** Dry/Wet control for Metallic textures

- **Blur Effect:** Wet/Dry control, Blur length (delay time)

- **Flanger:** Wet/Dry control, LFO rate for modulation speed

- **EQ Section:** High frequency shelf EQ, Mid frequency band EQ, Low frequency shelf EQ

Each effect is mapped for live expression, designed for smooth performance use.

## Requirements

To run GhostEcho locally:

**Python 3.10+**

Install dependencies:

```
gradio==5.4.0
pydub==0.25.1
librosa==0.10.2.post1
soundfile==0.12.1
resampy==0.4.3
numpy==1.26.4
numba==0.59.1
llvmlite==0.42.0
scipy==1.13.1
python-osc==1.8.3
```

**Csound 6.18+ (Required)**

GhostEcho uses Csound to run all DSP algorithms.

Check installation:

```csound --version```

**FFmpeg**

Required by Pydub for MP3/WAV decoding and encoding.

## Installation

### 1. Clone the repository

```
git clone https://github.com/Daphnetaolll/GhostEcho
cd GhostEcho
```

### 2. Install Python dependencies

```
pip install -r requirements.txt
```

### 3. Install Csound
[Download from] (https://csound.com/download.html)

Ensure the csound command is available in your terminal.

### 4. Install ffmpeg
  - **macOS**: `brew install ffmpeg`
  - **Windows**: install ffmpeg and add it to PATH 

## Usage
### Run the Application

```
python app.py
```

### Studio Mode

1. Upload a WAV/MP3 file
2. Choose an effect mode
3. Adjust the intensity knob
4. Export audio (wav/mp3)

### Live Mode

1. Select your audio input (Microphone, Instrument, BlackHole, etc.)
2. Apply Selection
3. Start Live Csound
4. Enable effects
5. Adjust expressive parameters in real time
6. Perform live with pitch, ring mod, blur, and flanger effects



## System Architecture (Optional)
```
Browser (Gradio UI + Wavesurfer.js)
          │
          ▼
     Python Backend
          │
    OSC Communication
          ▼
   Csound DSP Engine
          │
          ▼
     Audio Output (DAC)

```

- UI controls send OSC messages to Csound

- Csound processes audio in real time

- Offline processing uses Python + Pydub

- Web UI handles playback, preview, and rendering

## License

MIT License 
