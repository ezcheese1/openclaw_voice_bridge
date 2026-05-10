# Openclaw Voice Bridge

A lightweight local voice bridge for OpenClaw that keeps the assistant brain in the normal chat session while adding browser-based push-to-talk and spoken replies.

It connects a browser userscript to local Wyoming services like:

- Piper for TTS
- faster-whisper for STT
- openWakeWord for wake-word detection

## Why this exists

OpenClaw’s normal web UI is great for chat, but sometimes you want a more natural voice loop without routing the assistant brain through another automation stack.

Hal Voice Bridge makes that possible by splitting responsibilities cleanly:

- **OpenClaw** stays the brain
- **the browser** handles the user interaction
- **the local bridge** handles TTS/STT/wake-word services

## Features

- browser push-to-talk
- spoken assistant replies through Piper
- STT through faster-whisper
- optional wake-word plumbing through openWakeWord
- nginx-friendly same-origin proxy path (`/voice-bridge`)
- Tampermonkey userscript for the OpenClaw Control UI
- systemd service install
- uninstall script
- compact/minimized widget UI
- stop-speaking control

## Architecture

Browser → `openclaw_voice.user.js` → `/voice-bridge` → Wyoming services  
Browser → OpenClaw Control UI → normal assistant session

That means the assistant still replies normally in chat, while voice is layered on top instead of replacing the core workflow.
