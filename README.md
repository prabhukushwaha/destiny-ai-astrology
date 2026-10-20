# Destiny AI Astrology

Connect Claude to the **Destiny AI** remote Vedic-astrology engine. This plugin registers
the Destiny AI MCP server and installs a gateway skill so Claude produces grounded,
chart-based readings instead of guessing from general knowledge.

## What it does

Claude answers astrology questions by calling the `get_reading` tool on the Destiny AI
server, which runs a full Vedic pipeline (houses, planets, divisional charts, strengths,
avasthas, dashas, and transits). Supported questions include natal birth-chart
interpretation, relationship compatibility, dasha (planetary period) timing, and current
transit forecasts. A gateway skill enforces the `get_reading` loop so every answer is based
on a real computed chart.

## Install

```
/plugin install destiny-ai-astrology --marketplace prabhukushwaha/destiny-ai-astrology
```

## Required birth details

Before a reading, Claude needs your **name**, **date of birth**, **time of birth**, and
**city of birth**. For questions about current timing or transits, it also uses your
**current city**. You never need to provide coordinates — Claude geocodes cities for you.

## Setup

On **claude.ai** no setup is required — connect the server from the **Connectors** tab and
start asking. Requests from claude.ai are authorized at the network level, so an API key is
optional there. If you run the plugin from another client, or want per-user rate limits,
enter your **Destiny AI API key** when prompted; it is stored securely and sent as a bearer
token. Request a key at [destinyaiastrology.com](https://destinyaiastrology.com).

## Data

To generate a reading, Claude sends the birth details you provide (name, date, time,
and city of birth, plus your current city for transit questions) and your astrology
question over HTTPS to the Destiny AI MCP server at
`astroapi-prod-dsqvza5jza-ul.a.run.app`, authenticated with your API key. That server is
the only destination; the plugin sends no data anywhere else and runs no other code on your
machine. Handling of data received by the server is governed by the Destiny AI
[Privacy Policy](https://destinyaiastrology.com).

## Safety and disclaimer

Readings are for **self-reflection and entertainment only** and are **not** medical, legal,
financial, or psychological advice. The chart describes tendencies, not fixed fate. Destiny
never diagnoses health conditions, never advises on treatment, and never predicts lifespan
or the time or manner of death. For health, legal, or financial concerns, consult a
qualified professional.
