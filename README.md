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

Before a reading, Claude needs your **date of birth**, **time of birth**, and **city of
birth**. For questions about current timing or transits, it also uses your **current city**.
You never need to provide coordinates — Claude geocodes cities for you, and Claude never asks
for your name or email.

## Setup

The first time Claude uses a Destiny tool, it asks you to **sign in with your Destiny
account** (Sign in with Apple, Google, or email). Use the same account as in the Destiny
app; there is nothing else to configure. Each account has a daily allowance for readings,
chart tools and compatibility that follows its Destiny plan; the allowance resets at
00:00 UTC.

In Claude Code, add the server and sign in from `/mcp`:

```
claude mcp add --transport http destiny https://mcp.destinyaiastrology.com/mcp/jsonrpc
```

## Data

To generate a reading, Claude sends the birth details you provide (date, time and city
of birth, plus your current city for transit questions) and your astrology question over
HTTPS to the Destiny AI MCP server at `mcp.destinyaiastrology.com`, authenticated with the
access token from your Destiny sign-in (the token carries no email or birth data). That server is
the only destination; the plugin sends no data anywhere else and runs no other code on your
machine. Handling of data received by the server is governed by the Destiny AI
[Privacy Policy](https://destinyaiastrology.com).

## Safety and disclaimer

Readings are for **self-reflection and entertainment only** and are **not** medical, legal,
financial, or psychological advice. The chart describes tendencies, not fixed fate. Destiny
never diagnoses health conditions, never advises on treatment, and never predicts lifespan
or the time or manner of death. For health, legal, or financial concerns, consult a
qualified professional.
