# Project Overview - **bmp-dash**

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


# Scheduling Module: Action Plan

Ordered list of tasks to gradually build the Scheduling Module. We’ll tackle these steps one by one.

*- Consider making and attaching [wireframes](#) as we go.*  
*- Adjust scope and reorder tasks if needed based on feedback or new realizations.*
*- Check things off as done as we go.*  
*- Push hard to reach deadlines. Simplify if needed.*  
*- Check-in with user team regularly.*  
*- Be mindful of feature creep to ensure meaningful progress.*  
*- Continually consider interplay with other modules to spiral/pivot effectively.*

---

### 0.0 – User & Access Foundations  
**Deadline:** May 16, 2025  
- [ ] Sync `personnel` table ⇄ `auth.users` (Supabase Auth)  
- [ ] Build **User Profile** page with basic info  
- [ ] Add `departments`, `subdepartments`, and `roles` tables in Supabase  
- [ ] Define and enforce **access control** (RLS policies, UI guards)  
- [ ] **Demo** access control strategy (navbar, page, data, UI element)  
- [ ] Create relevant **documentation**?

---

### 0.1 – Read-Only Import & Data Cleaning  
**Deadline:** May 16, 2025  
- [ ] **Polish** one-way import flow: Office Scripts parser ⇄ Power Automate call  
- [ ] **Review** release column brainstorming docs, Appsheets tables, master schedule columns, & traveler fields.  
- [ ] **Finalize and document** official `release` table columns
- [ ] **Fix** column mapping from Excel/E2 to Releases fields  
- [ ] Finish Excel **VBA macro** for addressing duplicates and other manual data cleanup  
- [ ] **Plan** for data normalization: handle duplicates and SKU variants via mapping rules or lookup table  

---

### 0.2 – Basic Release Table  
**Deadline:** May 17, 2025  
- [ ] **Define** `Releases` schema in Supabase  
- [ ] Implement fetch of **Master Schedule import-flow**
- [ ] Execute **initial import** into Supabase  
- [ ] Scaffold **Releases page** with `material-react-table`
- [ ] Wire up API call to **fetch and render** Releases  

---

### 0.3 – Table UI Features – Review Rollout  
**Deadline:** May 17, 2025  
- [ ] **Rollout Plan:** research and determine how and when to add these UI controls  
    - Filters: *multiselect, date, department, status*
    - Search: *global text & column-specific*  
    - Hide/Show & Sort Columns: *backend has extra fields; tailor per work-area; allow end-user customization*
    - Settings Save: *persist table layout and filter settings per user*

---

### 0.4 – Basic Release Detail  
**Deadline:** May 18, 2025  
- [ ] List **fields and sections** (BOM, traveler ops, inventory summary, images) & plan layout  
- [ ] Scaffold **Detail View page** (route, layout, crucial fields)  
- [ ] Hook up **data fetching** for selected release  
- [ ] Scaffold **Form View**  
- [ ] Implement **data submission** to Supabase
- [ ] Add **read/write toggle** and associated conditional rendering  

---

### 0.5 – Production Clocking  
**Deadline:** May 20, 2025  
- [ ] Define data model, **add tables** in Supabase (`release_events`?`operator_events`?)
- [ ] **Map** action button logic (Setup → Production → Teardown, with Pause rules)  
- [ ] **Add action buttons** to detail view  
- [ ] **Implement** timer and conditional logic  

---

### 0.6 – Grouping & KPI Lines  
**Deadline:** May 24, 2025  
- [ ] **Explore** grouping and subtotal techniques in **MTR**  
- [ ] Create **dynamic week grouping** feature  
- [ ] Define and implement **dynamic department KPI lines** (consider using MTR subtotals)  
- [ ] Address banner-row **export problem** from Master Schedule: KPI/week rows aren’t real releases and must be excluded from the data array but shown in sequence  
- [ ] Render **legacy week & KPI lines** in the table  
- [ ] Set up **toggle button** and conditional rendering  

---

### 0.7 – Kitting & Purchasing Basics  
**Deadline:** May 25, 2025  
- [ ] Design/find MRT in-cell **progress bar**
- [ ] Reveal kitting and purchasing status columns in `release` table
- [ ] Create Kit **progress** columns and calculations *(components kitted vs. total)*
- [ ] Create Purchasing columns and calculations
  - [ ] fraction of **required materials** ordered/stocked
  - [ ] fraction of **placed POs** received
- [ ] Implement progress bars
  
---
## *BRAKEPOINT*
***Switch focus** to Inventory Module (add tables for kits, lots, etc) then return here*

---
### 0.8 – Kitting & Purchasing Continued


  **Deadline:** *After Inventory Module’s first breakpoint*

 
- [ ] Tailor kitting table into a **Kitting Schedule** view…  
- [ ] **Review** Inventory module (purchasing to-do list, etc.) to identify further complementary features; add to this plan  
- [ ] **Build** remaining required kitting and purchasing features
- [ ] **Demo** and institutionalize on the shop-floor

---

### 0.9 – Extended Feature Backlog  
**Mid-Project Review**

*Take notes*
- Is production manager happy? Issues?
- Supervisor?
- Is kitting schedule up?
- Is purchasing/receiving schedule up?  
- Any additional features associated with Inventory Module?  

**Roadmap** for features ranked for future sprints:  
1. Operations Table import & editing (traveler details), clocking v3  
2. Gantt / Timeline view  
3. Related KPIs, Ideal Load Planning heatmaps (done in KPIs module?)  
4. Inline editing features  
5. Inline expanding detail pane (KPI graphs, etc.)  
6. Bulk Actions & Schedule Templates  
7. Alerts & Notifications  
