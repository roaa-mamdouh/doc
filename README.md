## Atlas

| **Project Phase**     | **Key Actions**                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| **Kickoff & Analysis**   | • Identify stakeholders, goals, scope.<br>• Audit ERPNext/Frappe (Tasks, Timesheet, Raven, etc.).<br>• Document requirements (use BRD/user-stories template:contentReference[oaicite:48]{index=48}). |
| **Design & Planning** | • Map ClickUp features to ERPNext modules (see comparison table).<br>• Prototype missing UIs (e.g. workload planner).<br>• Plan custom development tasks (sprints) and milestones. |
| **Development**       | • Implement in iterations: enhance Task/Project, Timesheet, Gantt, Kanban.<br>• Build custom apps or scripts for gaps (workload view, recurring tasks).<br>• Regularly update docs and run demos. |
| **Testing & Review**  | • Use ERPNext reports to verify data (timesheets, task status).<br>• Get user feedback each sprint; adjust scope.<br>• Update requirements/docs as features evolve. |
| **Deployment & Handover** | • Migrate to production (Frappe Cloud or in-house server).<br>• Train users on new tools (Raven chat, Planner, etc.).<br>• Establish support process (e.g. helpdesk channel). |


# Project Documentation: ClickUp Alternative in Frappe (Codename: Atlas)  
> **Prepared by:** Roaa
> **Date:** 9/5/2025 
> **Version:** 1.0  
> **Status:** Ongoing  

---

## 🔷 Executive Summary

We're building a modern, Frappe-based alternative to ClickUp to manage tasks, projects, time tracking, and team collaboration — fully integrated with our ERPNext ecosystem. The goal is to minimize dependency on third-party tools, improve productivity workflows, and customize the experience based on internal needs.

---

## 🔷 Codename: Atlas

The project is temporarily named **Atlas** — a symbolic name suggesting a platform that can “carry the team” and “map out” projects and tasks.

---

## 🔷 High-Level Goals

| Goal | Description |
|------|-------------|
| 🧩 Build Core Project Features | Implement task, time tracking, and workload management features natively in Frappe |
| 🔁 Reduce ClickUp Dependence | Gradually shift operations from ClickUp to Frappe as features stabilize |
| 🧠 Encourage Internal Use | Promote the use of Raven, Gameplan, and Drive to learn what works and how to integrate them |
| 📚 Improve Business Documentation | Use this project as a model for proper Business Analysis and Documentation workflows |

---

## 🔷 Feature Comparison Matrix: ClickUp vs ERPNext

| Feature Category | ClickUp | ERPNext / Frappe (Current) | Status / Plan |
|------------------|---------|----------------------------|----------------|
| ✅ Tasks | ✅ Full-featured task hierarchy, assignments, subtasks, dependencies | ✅ ERPNext "Tasks" module supports basic tasks, assignments, and statuses | Extend with Subtasks + Dependencies |
| ✅ Projects | ✅ Nested folders, tags, views | ✅ ERPNext "Projects" module with milestones | Use existing, enhance UI |
| ✅ Time Tracking | ✅ Native, with start/stop timers and manual logs | ⚠️ Limited in ERPNext: manual time logs only | Build a start/stop timer; sync with Tasks |
| ✅ Workload View | ✅ View workloads per user, per week | ❌ Missing in ERPNext | Custom view on Task assignments + hours |
| ✅ Comments / Activity | ✅ Comment threads, mentions, activity log | ✅ Basic commenting exists | Extend with @mentions, richer UX |
| ✅ Board View | ✅ Fully interactive Kanban | ✅ Exists in Frappe (Kanban Board) | Use and extend |
| ✅ Docs/Wiki | ✅ Built-in doc editing + sharing | ✅ Use Frappe Drive or Wiki | Integrate Drive/Wiki more tightly |
| ✅ Reminders & Notifications | ✅ Per-task reminders, email/push notifications | ✅ Email and in-app, but limited | Enhance notifications UX |
| ✅ Dashboards | ✅ Fully customizable dashboards | ⚠️ Reports exist, dashboards need setup | Build project dashboards |
| ✅ Goals / OKRs | ✅ Goal tracking | ❌ Not available | Optional Phase 2 feature |
| ✅ Forms & Automations | ✅ Form creation, automations, conditions | ⚠️ Frappe Workflow exists but less flexible | Use Workflow + JS scripting |

---

## 🔷 Module Extension Plan

### Phase 1: **Core Foundations**

| Module | Action |
|--------|--------|
| `Projects` | Audit and clean project creation, linking Tasks correctly |
| `Tasks` | Add support for: Subtasks, Dependencies, Priorities, Time Estimates |
| `Timesheets` | Add native Timer functionality (start/stop per task), auto-log time |
| `Users / Roles` | Define roles: Team Member, PM, Admin |

### Phase 2: **UX Features**

| Feature | Action |
|--------|--------|
| Workload View | Custom page showing user-wise task loads for a week |
| Activity Logs | Add full logs per task/project: comments, time logs, changes |
| Notifications | Custom notification framework: due date alerts, mentions |
| Dashboards | Custom dashboards for PMs: ongoing tasks, workloads, time logs |

### Phase 3: **Advanced (Optional)**

| Feature | Action |
|--------|--------|
| Automations | Rule-based workflows for task status changes, reminders |
| Goals / OKRs | Track outcomes tied to projects/tasks |
| AI Suggestions | (Optional) Suggest task reassignments, reminders based on load |

---

## 🔷 Architecture Proposal

- Built entirely in **Frappe App** (`frappe_clickup` or `atlas`)
- Extend existing `projects` and `tasks` doctypes
- New custom pages for:
  - Timer UI
  - Workload View
  - Project Dashboard
- Use Raven for async updates, activity feeds
- Use Frappe Drive / Wiki for internal docs

---

## 🔷 Development Milestones

| Milestone | ETA | Owner |
|----------|-----|-------|
| Audit ERPNext Tasks & Timesheets | Week 1 | You |
| Build Timer MVP | Week 2 | You |
| Create Workload Report View | Week 3 | You + Frontend |
| Migrate 1 Team from ClickUp to Atlas | Week 4 | You + PM |
| Refine Features + Document Usage | Week 5–6 | You |

---

## 🔷 Business Analysis Process

| Area | Practice |
|------|---------|
| Feature Discovery | Reverse-engineer ClickUp usage + Interview team |
| Functional Requirements | User stories + feature comparison like above |
| Technical Feasibility | Start from ERPNext base and assess gaps |
| Continuous Feedback | Weekly demos with PM/Boss |
| Living Documentation | Update this doc weekly with progress and new ideas |

---

## 🔷 How You’ll Know If Core Features Exist Already

1. **Search ERPNext Docs & GitHub:**  
   - Look up “Tasks,” “Projects,” “Time Logs” in [ERPNext Docs](https://docs.erpnext.com/)  
2. **Use Bench Console:**  
   - Run: `frappe.get_meta("Task").fields` to inspect doctypes  
4. **Explore the UI Yourself:**  
   - Use Raven, Gameplan, Projects, etc. in real life  
5. **Trace Functionality in Code:**  
   - Trace from UI > JS > Python Controller > Doctype  
