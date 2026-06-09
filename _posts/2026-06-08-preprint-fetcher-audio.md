---
title: "Preprint Fetcher just got an audio upgrade"
date: 2026-06-08
author: "Gabriella Estevam"
layout: post
permalink: /writing/preprint-fetcher-audio/
body_class: writing-page
---


After several months of using <a href="https://gabriellaestevam.com/writing/preprint-fetcher/" style="background-color: #F7F0FD; font-family: Courier, monospace; padding: 2px 2px; color: #8806CE; text-decoration: none;"> Preprint Fetcher</a>, I can say that it has transformed my daily reading. My preprint feed is curated to my exact research interests, both project-specific and broad, and fully automated. Since the papers are pulled from bioRxiv daily, there is not much that I miss, and if there is a title that doesn't make it, I still have other RSS feeds and platforms that fill the gap.

I strive to begin each morning with reading, but on days where I am on-the-go, I'd still like to have a method to check my preprint feed. Therefore, I've now added a feature (again with the help of Sonnet 4.6) that converts the feed into audio, in addition to the local HTML bookmark update.

The full repository is live on my GitHub and bakes in the audio conversion using open source text-to-speech, which can be changed to suit specific audio preferences. Now, right when Preprint Fetcher runs for the day, it creates an MP3 which can be played locally through __`audio_feed.py`__{: .bold-color} or through an app like Apple Music.

Originally, I planned on building a full podcast-inspired experience where Preprint Fetcher would directly upload the audio feed into Spotify or Apple Music, complete with an intro, cover art, and other features I could use on a commute. That is still the vision, but will require more buildout, especially around the listening experience.

<br>

For now, here's how to implement Preprint Fetcher audio:

<br>

## Download scripts

- Found here in this  <a href="https://github.com/gestevam/preprint_fetcher_audio" style="background-color: #F7F0FD; font-family: Courier, monospace; padding: 2px 2px; color: #8806CE; text-decoration: none;"> Github repository</a>
- I also recommend setting up a virtual environment - instructions in the README

<br>


## Install Piper TTS

 <a href="https://github.com/OHF-Voice/piper1-gpl" style="background-color: #F7F0FD; font-family: Courier, monospace; padding: 2px 2px; color: #8806CE; text-decoration: none;"> Piper</a>  provides open source, in-browser text-to-speech (TTS), and requires no cloud subscriptions.
 <br>

```
pip install piper-tts
```


<br>

## Download voice model

This downloads the `libritts` voice model locally, and to switch to a different model change `VOICE_MODEL` path in `audio_feed.py` from the available voices on <a href="https://huggingface.co/rhasspy/piper-voices" style="background-color: #F7F0FD; font-family: Courier, monospace; padding: 2px 2px; color: #8806CE; text-decoration: none;"> Piper </a>. Again, no data leaves your machine during playback.

  ```
  mkdir -p ~/preprint-fetcher-audio/voices && cd ~/preprint-fetcher-audio/voices
  curl -LO https://huggingface.co/rhasspy/piper-voices/resolve/main/en/en_US/libritts/high/en_US-libritts-high.onnx
  curl -LO https://huggingface.co/rhasspy/piper-voices/resolve/main/en/en_US/libritts/high/en_US-libritts-high.onnx.json
  ```


<br>


## Test setup

This checks that: Piper is installed, the voice model exists, and audio plays.

  ```
  python test_audio.py
  ```


<br>

## Run the audio feed

Preprint Fetcher will generate an MP3 of the feed, including title, authors, and key findings extracted from the abstract.

  ```
  python audio_feed.py
  ```
<br>
To preview the script without generating audio:

  ```
  python audio_feed.py --list
  ```
<br>
To generate the MP3 without playing it:

  ```
  python audio_feed.py --no-play
  ```

<br>

## What to expect

Each paper is introduced as:

> *"Paper 1 of 5. [title]. By [first author] from the [last author] group, and colleagues. Key findings. [2-3 sentences extracted from the abstract]."*

The "key findings" are extracted from sentences containing phrases like "we show", "we found", "our results", and "importantly" from the abstract.

The the MP3 lives at __`feed_output/feed.mp3`__{: .bold-color} and can be shared to your phone or opened in any audio player.
