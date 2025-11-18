# Haitian Translator - Audio Splitter

A Google Colab project to download, process, and transcribe YouTube audio for Haitian translation purposes. This project splits audio files on silence and transcribes them using OpenAI's Whisper API.

## Features

* Download audio from YouTube videos
* Convert MP3 to WAV (16kHz, mono)
* Split audio into chunks based on silence
* Transcribe chunks using Whisper via OpenAI API
* Save transcriptions to JSON

## Requirements 

* Python 3.x
* `yt_dlp`
* `pydub`
* `librosa`
* `openai` (or your OpenAI client wrapper)
* `ffmpeg` installed on the system

Install dependencies with pip:
```bash
pip install yt-dlp pydub librosa openai
```
Ensure ffmpeg is installed and in your PATH.

## Usage

1. Open the notebook in Google Colab or your local Python environment.
2. Set your OpenAI API key in the `userdata` dictionary or as an environment variable.
3. Call the functions in order:
   ```python
   youtube_url = "YOUR_YOUTUBE_URL"
   output_name = "my_audio"
    
    
    # Extract YouTube ID (optional)
    youtube_id = extract_youtube_id(youtube_url)
    
    
    # Download audio
    download_audio(youtube_url, output_path=f"{output_name}.mp3")
    
    
    # Convert to WAV
    wav_path = convert_to_wav(f"{output_name}.mp3", output_path=f"{output_name}.wav")
    
    
    # Split audio on silence
    chunk_paths = split_audio_on_silence(wav_path, output_name)
    
    
    # Transcribe chunks
    transcript_data = transcribe_chunks(chunk_paths, output_name)
    
    
    # Save transcription
    save_transcription(transcript_data, output_file=f"{output_name}_transcription.json")
   ```
## Project Structure

```css
haitian-translator-audiosplitter/
 └── audiosplitter.ipynb   # Main Colab notebook with all code
```
