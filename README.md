## Atlas

| **Project Phase**     | **Key Actions**                                                                                         |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| **Kickoff & Analysis**   | • Identify goals, scope.<br>• Audit ERPNext/Frappe (Tasks, Timesheet, Raven, etc.) |
| **Design & Planning** | • Map ClickUp features to ERPNext modules (see comparison table).<br>• Prototype missing UIs (e.g. workload planner).<br>• Plan custom development tasks (sprints) and milestones. |
| **Development**       | • Implement in iterations: enhance Task/Project, Timesheet, Gantt, Kanban.<br>• Build custom apps or scripts for gaps (workload view, recurring tasks).<br>• Regularly update docs and run demos. |
| **Testing & Review**  | • Use ERPNext reports to verify data (timesheets, task status).<br>• Get team feedback each sprint; adjust scope.<br>• Update requirements/docs as features evolve. |
| **Deployment & Handover** | • Migrate to production.<br>• Train team on new tools (Raven chat, Planner, etc.).<br>• Establish support process (e.g. helpdesk channel). |


# Project Documentation: ClickUp Alternative in Frappe (Codename: Atlas)  
> **Prepared by:** Roaa
> **Date:** 9/5/2025 
> **Version:** 1.6  
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

---

## 🔷 Feature Comparison Matrix: ClickUp vs ERPNext

| **Feature** | **ClickUp** | **ERPNext/Frappe Equivalent** | **Status / Notes** |
|-------------|-------------|-------------------------------|--------------------|
| **Task Management** | Rich tasks: title, description, assignee, due date, priority, status, tags, attachments, comments, recurring tasks. | ERPNext Task doctype (Projects module)<br>Supports title, description, status, priority, assignee, due date. Tasks allow parent/child (subtasks) and “Depends On” for dependencies.<br>Comments and file attachments are built-in. Recurrence is not native (would need custom scripting). | Most basics covered. Recurring tasks would require custom work. |
| **Subtasks / Dependencies** | Unlimited nested subtasks, dependencies with automatic alerts. | ERPNext tasks allow grouping via *Is Group/Parent Task*. “Depends On” field for dependencies. Alerts on overdue tasks can be configured with Alerts/Notifications. | Largely supported. Dependencies exist; may need UI tweaks for convenience. |
| **Kanban & Board Views** | Drag-and-drop board views (To Do, In Progress, Done, etc.) | Kanban Board view for any DocType. You can create a Kanban on the Task doctype so tasks appear as cards in status columns and can be moved by drag/drop. | Built-in and configurable via Kanban Board (no code needed). |
| **Gantt / Timeline** | Interactive Gantt charts for project timelines. | ERPNext has Gantt charts for Projects (timeline, dependencies). Use Frappe Gantt library if needed. | Available in Projects module. |
| **Time Tracking** | Built-in timers on tasks (manual or auto), dashboards of hours. | ERPNext Timesheet with timer. Users log time per task/project in the Timesheet. Activity Types and Costs can be defined. Time logs feed into HR/payroll/billing if needed. | Time tracking is fully supported. The Timesheet UI even has a Start Timer dialog for tasks. |
| **Workload / Capacity** | Workload View: visual capacity planning per user (by hours, tasks, or points). | No direct equivalent. ERPNext does not ship a user-capacity workload chart out-of-the-box. The Planner (Prototype) app offers a simple task-assignment schedule. You can build custom reports or use Frappe Charts to visualize hours-per-employee. | **Gap:** Will require customization (or use Planner as a starting point). |
| **Recurring Tasks** | Repeatable tasks (daily/weekly/monthly). | ERPNext tasks do not support recurrence natively. A custom script or doctype (e.g. use ToDo or Scheduler actions) would be needed. | Not built-in; mark for custom development. |
| **Reminders / Notifications** | Automatic reminders, email/push alerts. | ERPNext has Notifications and Event Reminders (Emails on task deadlines, etc). Raven can send chat notifications or messages when tasks change. | Covered by ERPNext alerts and Raven integrations. |
| **Chat & Collaboration** | In-app chat/comments, Slack/Teams integrations. | Use Raven for team chat (built on Frappe). Raven channels can link to Projects or Tasks, sending notifications on events. ERPNext also has Comments on records. No built-in Slack, but external bots or webhooks could be added. | Chat is provided by Raven (optional); ERPNext itself has comment threads. |
| **Dashboards & Reporting** | Custom dashboards of tasks, time, goals. | ERPNext Dashboards (for Projects, Time Log, etc) can be built via the Dashboard module. Reports (task lists, time reports) are available or customizable. Charts (bar/line) can show time spent. | ERPNext’s reporting tools cover basic needs; additional custom reports can be created. |
| **Integrations / APIs** | ClickUp API, Zapier, etc. | Frappe/ERPNext is open-source with REST APIs for all doctypes. Custom Frappe apps can integrate with external services or AI agents (via Raven). | Full integration potential via APIs. |


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
| Workload View (Planner Prototype) | Custom page showing user-wise task loads for a week |
| Activity Logs | Add full logs per task/project: comments, time logs, changes |
| Notifications | Custom notification framework: due date alerts, mentions |
| Dashboards | Custom dashboards for PMs: ongoing tasks, workloads, time logs |

### Phase 3: **Advanced (Optional)**

| Feature | Action |
|--------|--------|
| Automations | Rule-based workflows for task status changes, reminders |
| Goals | Track outcomes tied to projects/tasks |
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





# Atlas Task Management System - Project Plan


**[Expected User Experience:](https://roaa-mamdouh.github.io/doc/)**

Framework: Frappe UI

### Database Design

#### Core Atlas Task Schema

```sql
atlas_task
├── Basic Information
│   ├── name (Primary Key)
│   ├── title
│   ├── description
│   ├── priority (High/Medium/Low)
│   └── status (Open/In Progress/Review/Pending Mina/Completed/Cancelled)
├── Assignment & Ownership
│   ├── assigned_to (Link to Employee)
│   ├── assigned_by (Link to Employee)
│   ├── project (Link to Project)
│   └── department (Link to Department)
├── Timeline Management
│   ├── expected_start_date
│   ├── expected_end_date
│   ├── actual_start_date
│   ├── actual_end_date
│   └── estimated_hours
├── Progress Tracking
│   ├── progress_percentage
│   ├── actual_hours
│   ├── remaining_hours
│   └── completion_date
└── Additional Features
    ├── tags (Table MultiSelect)
    ├── dependencies (Table - Link to other Atlas Tasks)
    ├── attachments (Attach)
    └── custom_fields (Extensible)
```

## Phase-by-Phase Development Plan

### Phase 1: Foundation & Core Setup (Week 1)

**Week 1: Environment Setup & Analysis, Task DocType Development**

**Deliverables:**
- Requirements gathering and documentation
- Team Input Collection: Conduct ClickUp feature audit with current users (must-have vs nice-to-have)
- Core doctype creation:
  - Field definitions and validations (matching ClickUp data structure)
  - Basic form layout design with modern UI components
  - List view configuration with filtering and sorting capabilities

**Success Criteria:**
- Atlas Task doctype created with all essential fields
- Basic CRUD operations functional
- Development environment fully operational

### Phase 2: Workload Visualization Module (Weeks 2-3)

**Status:** In Progress (80% Complete)

**Week 2: Dashboard Foundation & Core Visualization**

**Deliverables:**
- Complete current workload view implementation
- Bug fixes and performance optimization for existing 80% complete module
- User testing and feedback integration (Mina's Feedback)

**Success Criteria:**
- Workload visualization fully functional and tested
- Real-time updates working across multiple users

**Week 3: Mobile Responsiveness & Integration**

**Deliverables:**

*Days 1-3: Mobile interface optimization*
- Responsive design for dashboard and workload views
- Push notifications for task updates and mentions

*Days 4-5: ERPNext Module Integration*
- Timesheet integration (automatic time tracking from tasks)

### Phase 3: Advanced Features & ClickUp Parity (Weeks 4-5)

**Week 4: Workflow Engine & Collaboration**

**Deliverables:**

*Days 1-3: Custom workflow development*
- State transition logic (Open → In Progress → Review → Pending Mina → Completed)
- Automated notifications (assignment, due dates, mentions)

*Days 4-5: Collaboration Features* #needs to be reviewed
- Comments system with rich text and file attachments
- @mentions functionality with notifications
- Task watchers system (subscribe to task updates)
- Activity timeline (audit trail of all task changes)

**Week 5: Reporting & Analytics Dashboard**

**Deliverables:**

*Days 1-3: Custom reports development*
- Task completion reports (team and individual performance)
- Team productivity analytics (velocity, burndown charts)

*Days 4-5: Dashboard widgets & KPIs*
- Real-time metrics dashboard (tasks completed, overdue, in progress)
- Customizable dashboard layouts (user-specific views)
- Executive summary widgets (high-level project health)

### Phase 4: API Development & Raven Integration (Week 6)

### Phase 5: Testing & Quality Assurance (Week 7)

**Week 7: Comprehensive Testing**

**Deliverables:**

*Days 1-2: Automated testing suite*
- Unit testing (server-side logic, frontend components)
- Integration testing (cross-module functionality)
- API endpoint testing (performance and reliability)

*Days 3-5: User Acceptance Testing*
- Stakeholder testing sessions with ClickUp power users
- Feature validation against ClickUp functionality checklist
- Performance benchmarking vs ClickUp response times
- Security testing and vulnerability assessment
