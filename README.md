# IQAir Air Quality Skill for OpenClaw

Real-time air quality monitoring with visual AQI indicators for OpenClaw AI agents.

## Features

- 🌍 Global air quality data from IQAir API
- 🎨 Color-coded AQI levels (🟢 Good → 🟤 Hazardous)
- 📍 City name or GPS coordinate lookup
- 🌤️ Auto-triggers on weather queries

## Installation

```bash
clawhub install iqair
```

Or install from this repository:
```bash
git clone https://github.com/atesluks/openclaw-skill-iqair.git
cp -r iqair-openclaw-skill ~/.openclaw/workspace/skills/iqair
```

## Setup

1. Get a free API key from the [IQAir Dashboard](https://dashboard.iqair.com/personal/api-keys) (free Community plan)
2. Add it to your OpenClaw config (`~/.openclaw/openclaw.json`) using one of these methods:

**Option A: Skill-specific (recommended for a single skill)**
```json
{
  "skills": {
    "entries": {
      "iqair": {
        "env": {
          "IQAIR_API_KEY": "your_key_here"
        }
      }
    }
  }
}
```

**Option B: Global environment variables (recommended for multiple skills)**
```json
{
  "env": {
    "vars": {
      "IQAIR_API_KEY": "your_key_here"
    }
  }
}
```

## Usage

The skill automatically triggers when you ask about air quality or weather:

### Examples:
```bash
• "What's the weather in Dubai?"
• "How's the air quality in Riga?"
• "Is it safe to go outside in Beijing?"
```

### Response:
```bash
🟠 113 - Unhealthy for Sensitive Groups
Dubai, United Arab Emirates
```

## AQI Levels
| AQI        | Level                          | Health Impact                                                      |
| ---------- | ------------------------------ | ------------------------------------------------------------------ |
| 🟢 0-50    | Good                           | No health concerns                                                 |
| 🟡 51-100  | Moderate                       | Unusually sensitive people should limit prolonged outdoor exertion |
| 🟠 101-150 | Unhealthy for Sensitive Groups | Sensitive groups should reduce outdoor exertion                    |
| 🔴 151-200 | Unhealthy                      | Everyone should reduce outdoor activities                          |
| 🟣 201-300 | Very Unhealthy                 | Health alert - avoid outdoor activities                            |
| 🟤 301+    | Hazardous                      | Emergency conditions - stay indoors                                |

## Requirements

• OpenClaw AI agent
• Python 3.x
• Free IQAir Community API key (5 calls/min, 500/day, 10,000/month)