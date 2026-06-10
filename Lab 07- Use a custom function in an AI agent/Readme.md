# Astronomy Observation Assistant

## Use Case Story

### Scenario: Mr. Sam Plans an Astronomy Observation Session

- 👨‍🚀 **Mr. Sam** is an amateur astronomy enthusiast who wants to observe an upcoming celestial event using a telescope.
- 🔭 Instead of searching through astronomy websites and event calendars, he asks the Astronomy Assistant for help.
- 🌠 The assistant checks which astronomical event is coming up next and is visible from Sam’s region.
- 💰 After choosing an event, Sam wants to know the cost of booking a telescope.
- 📋 Once Sam confirms the observation details, the assistant prepares a professional observation report.
- ⏱️ This saves Sam time by avoiding manual research, calculations, and paperwork.
- ✅ Mr. Sam can quickly plan and organize his astronomy observation session with all the required information in one place.

---

# Code Development Overview

## Overall Purpose

- Creates an Astronomy Observation Assistant using Azure AI Agents.
- Helps users find astronomical events, calculate telescope costs, and generate observation reports.

## Agent Workflow

### 1. Startup Process

1. Loads environment configuration.
2. Connects to Azure AI Project and OpenAI services.
3. Creates a temporary astronomy agent.

### 2. Agent Tools

#### Tool 1: Next Visible Event

**Purpose:** Find the next astronomical event visible from a selected region.

**Inputs**
- Location

**Outputs**
- Event name
- Event type
- Event date
- Visibility regions

#### Tool 2: Observation Cost Calculator

**Purpose:** Calculate telescope rental costs.

**Inputs**
- Telescope tier
- Observation hours
- Priority level

**Formula**
```text
Base Cost = Hourly Rate × Hours
Total Cost = Base Cost × Priority Multiplier
```

#### Telescope Rates

| Tier | Rate/hr |
|------|----------|
| Standard | $50 |
| Advanced | $120 |
| Premium | $300 |

#### Priority Multipliers

| Priority | Multiplier |
|----------|------------|
| Low | 1.00 |
| Normal | 1.25 |
| High | 1.75 |
| Urgent | 2.50 |

#### Tool 3: Observation Report Generator

**Purpose:** Generate a detailed observation report.

**Inputs**
- Event name
- Location
- Telescope tier
- Hours
- Priority
- Observer name

## Supported Astronomical Events

- Quadrantids Meteor Shower
- Annular Solar Eclipse
- Total Lunar Eclipse
- Lyrids Meteor Shower
- Jupiter–Venus Conjunction
- Saturn–Mars Conjunction
- Partial Solar Eclipse
- Perseids Meteor Shower
- Geminids Meteor Shower

## Architecture Overview

```text
User
 ↓
Azure AI Agent
 ↓
Chooses Tool
 ↓
Business Logic
 ↓
Reads Event & Pricing Data
 ↓
Returns Result
 ↓
Agent Generates Response
 ↓
User
```

## Strengths

- Clear separation between agent and tools
- Input validation
- Multi-step tool orchestration
- Easy extensibility

## Limitations

- Static event data
- Limited location support
- Text-based reports
- No database persistence
- Agent recreated on each run

## Summary

The Astronomy Observation Assistant is a tool-calling AI agent that discovers celestial events, calculates telescope booking costs, and generates observation reports.
