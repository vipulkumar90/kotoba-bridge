# Kotoba Bridge

Kotoba Bridge is an AI-powered Discord bot that performs intelligent, context-aware translation between English and Japanese.

Unlike traditional translation bots, Kotoba Bridge considers previous messages in the conversation to generate translations that preserve meaning, tone, humor, and conversational flow.

The project is designed around a provider-agnostic AI architecture, allowing different LLM providers (Gemini, OpenAI, Anthropic, local models, etc.) to be swapped with minimal code changes.

---

## Goals

- Translate English ↔ Japanese automatically
- Preserve conversational context
- Preserve emojis, formatting, mentions, and Markdown
- Produce natural translations rather than literal ones
- Keep the AI provider completely abstracted
- Make the project easy to extend and maintain

---

## Features

### Automatic Language Detection

Messages are automatically detected as English or Japanese.

- English → Japanese
- Japanese → English

No commands are required.

---

### Context-Aware Translation

Instead of translating a message in isolation, the bot includes recent conversation history to improve translation quality.

Example:

```
Alice:
I'm moving next month.

Bob:
That's exciting!

Alice:
I see.
```

A normal translator might interpret "I see" literally.

Kotoba Bridge understands the conversation and generates a natural translation.

---

### AI Provider Abstraction

The application is built around an abstract AI interface.

Current planned providers:

- Gemini
- OpenAI
- Anthropic
- Mock provider for testing

Future providers can be added without changing the Discord bot.

---

### Conversation Context

The bot stores recent conversation history for each channel.

This context is sent to the AI during translation to preserve meaning and tone.

---

### Discord-Friendly Translation

The bot preserves:

- Mentions
- Emojis
- Markdown
- URLs
- Code blocks
- Discord formatting

---

## Planned Features

- Channel whitelist
- Channel blacklist
- Per-user language preferences
- Translation caching
- Conversation persistence
- SQLite support
- PostgreSQL support
- Translation editing when original messages are edited
- Delete translated messages when originals are deleted
- Slash commands
- Metrics and logging

---

## Architecture

```
Discord
      │
      ▼
Translation Service
      │
      ▼
Context Manager
      │
      ▼
Prompt Builder
      │
      ▼
AI Provider
      │
      ▼
Gemini / OpenAI / Anthropic
```

The Discord layer never communicates directly with any AI provider.

---

## Design Principles

- Modular
- Provider-agnostic
- Easily testable
- Clean separation of concerns
- Minimal coupling
- Extensible architecture

---

## Tech Stack

- Python
- discord.py
- Google Gemini API
- SQLite (optional)
- PostgreSQL (future)
- GitHub Actions (CI)

---

## Status

Currently under active development.
