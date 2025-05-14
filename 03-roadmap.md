# Feature Roadmap – bmp-dash

## 🔁 Development Strategy

This roadmap is organized by **phases and sprints**, focused on delivering a functional, scalable MVP. We prioritize simplicity, maintainability, and low-friction deployment, especially given the single-dev reality.

---

## 🚀 Phase 1 – MVP Foundations

### 🧩 Sprint 1: Auth + User Profiles
- Supabase Auth w/ Google & Microsoft providers
- Link authenticated users to personnel table
- Display basic user profile (photo, name, roles)
- Set up role-based permissions with Supabase RLS

### 📋 Sprint 2: Training + Personnel Management
- Personnel table with full CRUD
- Training event table + training record tracking
- Assign roles to personnel
- Record training completions + signatures

### 📦 Sprint 3: Inventory + Kitting Basics
- Inventory items table (GSheet import)
- BOM references from releases
- Kit creation UI for production runs
- Basic inventory adjustment + transaction history

### 🛠 Sprint 4: Maintenance + Quality Logs
- Equipment table
- Maintenance request + completion log
- QC inspection log table
- Link QC issues to releases or part families

---

## 🧭 Phase 2 – Operational Scheduling + UX Flows

### 📆 Sprint 5: Work Center Flow & Scheduling
- Define operations and work centers
- Add routing steps to releases
- Drag-and-drop or bulk update schedule
- Filter by department or supervisor view

### 📈 Sprint 6: Dashboards + KPIs
- Department and management dashboards
- Role-based visibility
- Highlight overdue tasks, upcoming training, inventory levels

---

## 🌱 Phase 3 – Future Enhancements

- Realtime sync (e.g., Supabase subscriptions)
- Offline mode or resilience for poor Wi-Fi
- Supervisor approval workflows
- User notifications
- Print/label/QR integrations
- Public-facing job viewer for customers
- Integrate with external systems (e.g., accounting)

---

## ✅ Notes

- Sprints are not strictly time-boxed but should deliver small, self-contained feature sets.
- Each sprint will spawn one or more GitHub branches (e.g., `feat/inventory-core-v1`)
- MVP goals aim for usable internal tooling, not full automation or customer access yet.

