# Project Overview – bmp-dash

## 🧭 What is bmp-dash?

`bmp-dash` is a lightweight ERP system purpose-built for a small job shop specializing in sheet metal enclosures. 
Designed for ~40 personnel (with ~10-15 concurrent users), the app aims to simplify, unify, and digitize daily operations without excess bloat.

## 🎯 Core Goals

- Replace fragmented AppSheet + Google Sheets tooling with a centralized platform
- Enable role-based workflows for training, inventory, production, maintenance, quality, and KPIs
- Keep the UI snappy and intuitive using React + MUI
- Ensure security and access control using Supabase Auth and Row-Level Security (RLS)
- Build iteratively to support evolving needs without major refactors

## 🧑‍🤝‍🧑 Primary User Groups

- **General Manager** – oversight, admin privileges, reports, approvals
- **Supervisors / Leads** – assign work, approve records, monitor KPIs
- **Production Floor Operators** – submit logs, access work orders or training info
- **Shipping / Logistics / HR / Quality / Maintenance** – role-specific dashboards & forms

> 🔍 For a full breakdown of shop floor and admin roles, see [`roles.csv`](../path/to/roles.csv) or the Supabase roles table.

## 🏗️ Architecture

| Layer         | Tech                          | Notes |
|---------------|-------------------------------|-------|
| Frontend      | React (Vite + MUI Toolpad Core) | Fast and modular UI toolkit |
| Backend       | Supabase (PostgreSQL)         | Relational DB with built-in API |
| Auth          | Supabase Auth                 | Google/Microsoft sign-in, RLS enforcement |
| Hosting       | Namecheap → `bullmetal.app`   | Frontend deployed here |
| Realtime & RPC| Supabase Edge Functions       | Optional for secure business logic |

> ⚠️ Supabase is our primary auth system, but we may revisit fallback auth providers (e.g., Firebase) if needs evolve.

## 🔁 Dev Philosophy

- **Minimal dev team**: Favor simplicity, leverage platform strengths — built by a single developer (for now), but designed for others to take over smoothly
- **KISS-first**: Don’t overbuild. Deliver usable features quickly
- **Composable**: Design code and data to scale without rewrites
- **Low friction**: Optimize UX for speed and clarity on the shop floor
- **Secure by design**: Limit frontend exposure, validate roles and access centrally

## ⏳ Current Status

- ✅ Firebase Auth replaced with Supabase Auth
- ✅ Initial schema for personnel + roles migrated from GSheets
- 🔄 Starting UX and MVP flow planning
- ⏳ Initial layout and components scaffolded

## 📌 Upcoming Milestones

- [ ] Design & implement user profile + role-based permissions
- [ ] Define MVP features and phase 1 sprints
- [ ] Build out training + personnel management module
- [ ] Integrate task manager tooling for dev tracking
