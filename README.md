# BLW Canada Dashboard (`dashboard.html`)

Single-file HTML dashboard for monitoring BLW Canada attendance and reporting health across **Cells**, **Services**, and **SG Overview**.

---

## What This File Does

- Loads dashboard data from a Google Apps Script endpoint
- Normalizes mixed payload shapes (weekly arrays, monthly objects, spark arrays)
- Classifies trends accurately (**no false growth from dips or missing reports**)
- Supports filtering, sorting, grouping, and tabbed views
- Renders sparkline previews on cards and detailed charts in a modal
- Highlights reporting quality and “Needs Attention” conditions
- Supports light/dark theme persistence via `localStorage`

---

## Data Source

The dashboard fetches data from:

- `API_URL` inside `loadDashboard()`
- Primary: JSONP (`loadViaJsonp`)
- Fallback: `fetch` with timeout (`fetchJsonWithTimeout`)

Expected payload:

```json
{
  "overview": [],
  "cells": [],
  "services": [],
  "lastUpdated": "ISO_TIMESTAMP"
}
