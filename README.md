# BLW Canada Dashboard (`dashboard.html`)

A single-file HTML dashboard for monitoring **attendance, trends, and reporting health** across **Cells**, **Services**, and **SG Overview** within BLW Canada.

---

## What This File Does

- Loads live dashboard data from a Google Apps Script endpoint
- Normalizes multiple data shapes (weekly, monthly, spark arrays)
- Classifies trends using **behaviour-based logic** (prevents false growth from dips or missing data)
- Supports filtering, sorting, grouping, and tabbed navigation
- Renders sparkline previews on cards and detailed charts in a modal
- Highlights reporting quality and actionable **Needs Attention** conditions
- Persists theme (light/dark mode) via `localStorage`

---

## Data Source

The dashboard retrieves data from:

- `API_URL` defined in `loadDashboard()`
- Primary method: JSONP (`loadViaJsonp`)
- Fallback method: `fetch` with timeout (`fetchJsonWithTimeout`)

### Expected Payload

```json
{
  "overview": [],
  "cells": [],
  "services": [],
  "lastUpdated": "ISO_TIMESTAMP"
}
