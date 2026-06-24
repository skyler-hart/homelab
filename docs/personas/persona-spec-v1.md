# Persona Specification v1.0

## Purpose

This specification defines the standard structure for all personas stored in this repository.

The goal is to ensure personas are:

- Portable across AI platforms
- Consistent in structure
- Suitable for role-playing
- Suitable for image generation
- Suitable for documentation examples
- Suitable for synthetic users and testing
- Easy to maintain and expand

All personas MUST conform to this specification.

---

# Directory Structure

Each persona shall exist in its own folder.

Example:

```text
personas/
├── persona-spec-v1.md
│
├── Jordan-Cross/
│   ├── Jordan_Cross_profile.md
│   ├── Jordan_Cross_prompts.md
│   ├── Jordan-Cross-Headshot.png
│   └── Jordan-Cross-Full-Length.png
│
├── Doug-Mercer/
│   ├── Doug_Mercer_profile.md
│   ├── Doug_Mercer_prompts.md
│   ├── Doug-Mercer-Headshot.png
│   └── Doug-Mercer-Full-Length.png
```

---

# Required Files

Every persona directory MUST contain:

| File | Purpose |
|--------|--------|
| First_Last_profile.md | Persona definition |
| First_Last_prompts.md | AI prompt collection |
| First-Last-Headshot.png | Canonical portrait |
| First-Last-Full-Length.png | Canonical full-length image |

Optional:

| File | Purpose |
|--------|--------|
| notes.md | Development notes |
| scenarios.md | Additional examples |
| timeline.md | Career history |
| voice.md | Writing style examples |

---

# Profile Format

Every First_Last_profile.md MUST contain the following sections.

Order should remain consistent.

# Name

## Overview

Required:

- Role
- Age
- Experience
- Location

Optional:

- Motto

---

## Biography

Describe:

- Background
- Career path
- Current role
- Motivations
- Areas of expertise

---

## Personality

Describe:

- Behavioral traits
- Communication tendencies
- Values
- Preferences

Use bullet lists.

---

## Goals

Professional objectives.

Use bullet lists.

---

## Frustrations

Professional pain points.

Use bullet lists.

---

## Core Skills

Technical and professional skills.

Use bullet lists.

---

## Communication Style

Describe:

- Tone
- Verbosity
- Preferred communication methods
- Typical responses

---

## Decision Framework

Describe how the persona evaluates decisions.

Prefer numbered lists.

Example:

1. Reliability
2. Security
3. Maintainability
4. Automation
5. Business value

---

## Strengths

Areas of exceptional capability.

Use bullet lists.

---

## Weaknesses

Known limitations and blind spots.

Use bullet lists.

---

## Preferred Technologies

Preferred tools, platforms, and methodologies.

Use bullet lists.

---

## Appearance

Required for image generation consistency.

Include:

- Gender
- Age range
- Hair
- Eyes
- Skin tone
- Height
- Build
- Clothing
- Distinguishing features

Avoid subjective descriptions.

Use observable characteristics.

---

## Canonical Images

Required.

Reference:

- First-Last-Headshot.png
- First-Last-Full-Length.png

---

## Common Scenarios

Required sections:

### Troubleshooting

How the persona approaches operational issues.

### Architecture Review

How the persona evaluates designs.

### Security Review

How the persona evaluates risk.

### Mentoring

How the persona teaches others.

Optional:

### Automation Design

### Incident Response

### Project Management

### Leadership

---

## Usage

Describe:

- Intended use cases
- Documentation scenarios
- Training scenarios
- Testing scenarios

---

# Prompt Format

Every First_Last_prompts.md MUST contain the following sections.

# Persona Name - AI Persona Prompts

---

## System Prompt

Defines:

- Identity
- Experience
- Personality
- Expertise
- Operating principles

This should be the primary prompt used across AI platforms.

---

## Troubleshooting Prompt

Operational issue investigation.

---

## Architecture Review Prompt

Design review.

---

## Change Management Prompt

Technology introduction or modification review.

---

## Security Review Prompt

Security evaluation.

---

## Mentoring Prompt

Teaching and coaching.

---

## Documentation Prompt

Documentation creation.

---

## Runbook Prompt

Operational procedure generation.

---

## Executive Briefing Prompt

Leadership communication.

---

# Image Standards

## LinkedIn Headshot

Requirements:

- Professional appearance
- Neutral background
- Chest-up framing
- Realistic lighting
- Corporate style

Recommended Size:

1024x1024

---

## Full Body Image

Requirements:

- Full-length view
- Professional environment
- Business or business-casual attire
- Realistic appearance

Recommended Size:

1024x1792

---

# AI Compatibility

Personas should work with:

- ChatGPT
- Claude
- Gemini
- Microsoft Copilot
- Grok
- Ollama
- Open WebUI
- AnythingLLM
- Local LLM deployments

Avoid:

- Platform-specific syntax
- Proprietary prompt formats
- Custom XML structures
- Tool-specific instructions

Prefer plain Markdown.

---

# Naming Conventions

Folder Names:

PascalCase with hyphens

Examples:

- Jordan-Cross
- Doug-Mercer
- Alex-Reed

Image Names:

- First-Last-Headshot.png
- First-Last-Full-Length.png

Markdown Files:

- First_Last_profile.md
- First_Last_prompts.md

---

# Versioning

Current Version:

v1.0

Future updates should preserve backward compatibility whenever possible.
