---
layout: post
title: "OPAL v1.3.0 release"
date: 2026-05-17
description: "The first major OPAL release under Amorphous Engineering."
---

## Full Changelog

### Execution viewer
- Tabbed execution detail UI (Meta / Operations / Data / BOM / Issues / Kitting), HTMX swap preserves URL state and scroll
- Per-operation focus in the Operations tab — sidebar lists ops, right pane shows only the selected op
- Captured-data audit table — flat table of every data_captured value across the run, multi-photo fields render as N image(s)
- NC step-hold — logging an NC puts the step in ON_HOLD with a banner; auto-resumes the moment every linked NC reaches a terminal disposition
- Execution gating from version snapshot — PENDING chip + main-pane label when prereq ops aren't terminal
- Redline / ad-hoc operations — operators can insert a whole rework op with disposition sub-steps into a running execution; the redline is anchored to its NC, shows a red REDLINE — IT-N banner above its sidebar tile linked to the issue, gates the host op until rework is done, and rides the NC disposition for approval

### Template authoring
- Tabbed editor shell (Meta / Operations / Flow / Kit / Outputs / Versions) matching the execution viewer
- Inline step editor — each step row in the Operations tab expands to a full editor; no separate step-edit page
- Drag-to-reorder for sidebar ops and main-pane sub-steps, with live renumbering (OP 1, OP 2, C1, `<parent>.<n>`)
- Flow tab — Resolve-style operation dependency graph, drag right-port → left-port to add edges; cycles and self-loops rejected
- Flow layout improvements (post-1.3.0 changelog) — barycenter row ordering + per-node row anchoring to prereqs (no more crisscross), auto-pan during edge drag, drop accepted anywhere on a node body
- Photo data-capture field type — single or multi-image per field; mobile triggers the camera natively
- Inline images in step instructions — drag-drop onto the textarea or click INSERT IMAGE; image renders inline in both editor and execution

### Other fixes
- Auto-updater no longer crashes on Textual app thread (regression from 1.2.1)
- Windows installer auto-adds install location to PATH
- Updater logs unparseable tags instead of silently returning None
- Updater raises a clear `RuntimeError` when the binary path is write-protected
- MCP server uses logging instead of stderr print
- Editor ops sorted by `order` (not by step-number label) so drag-reorder actually shows up
- `/api/attachments/upload` FK fields read from multipart form (silently dropped before)
- Sidebar drag-reorder works on `<a href>` rows (native link-drag suppressed)
- Inventory genealogy 500 fixed (`Part.part_number` → `internal_pn` in `core/genealogy.py`)