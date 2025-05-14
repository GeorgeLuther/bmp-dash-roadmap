✅ Finalized File & Folder Structure for bmp-dash-roadmap
📘 README.md
A living draft of the public-facing documentation for the actual ERP frontend (bmp-dash).

Will eventually migrate into the main app repo

Intro to what bmp-dash is, why it exists, how it works

📄 01-overview.md
A general summary of the system, who it’s for, core technologies, and scope.

High-level: roles, stack, deployment, philosophy

One of the first files new devs should read

🎨 02-ux-concepts.md
UX philosophy and cross-module design patterns.

Design values (clarity, speed, simplicity)

Navigation layout principles

Touch vs mouse logic

Visual standards and naming rules

🧱 03-modules/
One file per ERP module, defining the ideal state feature set, UX, and logic.

Think: Training, Inventory, Scheduling, Maintenance, etc.

Each file is a deep dive with end-goal clarity

Realistic + aspirational (what it would do if you had infinite time)

🗺️ 04-roadmap.md
The high-level development plan for building those modules and features in phases.

MVP → iterative improvements

Aligned to business priority

Connects directly to what’s in 03-modules/

✅ 05-work/ (Suggested name)
Tactical, granular breakdown of the roadmap into actionable units like:

sprints

milestones

feature sets

work packages

Each file contains:

Checklists

Tasks/subtasks

Design/code/infra/dev split

You can name files like:

sprint-01-auth-basics.md

milestone-inventory-core.md

training-phase-1-tasks.md
