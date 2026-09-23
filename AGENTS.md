# Muscle Pain Helper — Agent Guidelines

> **Repository Archetype**: `app` (Personal Health Tracking Application)
> **Rule Carrier SSOT**: `AGENTS.md` is canonical; `CLAUDE.md` is a symlink to this file.
> **Merge Authority**: Standard PRs with clean tests and review passing may be merged by agents per workspace standing grant.

## Overview

A lightweight personal application for tracking and managing muscle pain.

## Guidelines

1. **12-Factor Design**: Any future server or persistence logic should rely on standard environment variables.
2. **Rule Carrier SSOT**: All rules reside here in `AGENTS.md`. `CLAUDE.md` is a symlink to this file.
