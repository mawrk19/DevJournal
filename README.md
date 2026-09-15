# DevJournal: Developer-First Issue & Project Tracker with Embedded Dev Journal

**Version:** 1.0

**Stack:** Laravel 12, Inertia.js, React 19, Tailwind CSS, MySQL, Laravel Herd, Vite+

---

## 1. Introduction

### 1.1 Purpose

This document defines the software requirements for **DevJournal**, a streamlined, developer-first project and issue tracking application with native embedded developer journaling. It serves as the single source of truth for building, testing, and scaling the product using an enterprise-grade Laravel and React architecture.

### 1.2 Scope

DevJournal bridges the gap between traditional bloated project management software (like ClickUp/Jira) and personal developer workflows.

* **In-Scope:** Project management, status-driven ticket tracking, prioritization, markdown-supported inline developer logs/journals for traceability, and lightning-fast client-side navigation via Inertia.js.
* **Out-of-Scope:** Enterprise time tracking, billing/invoicing, multi-organization billing management, and external third-party Git webhook sync (reserved for v2.0).

### 1.3 Target Audience

* **Primary User:** Solo developers, indie hackers, and small engineering teams who want lightweight tracking coupled with a historical record of architectural decisions.

---

## 2. Overall Description

### 2.1 Product Perspective

DevJournal is built as a monolithic single-page application (SPA) wrapper using Laravel 12 for backend routing, authentication, and database integrity, combined with Inertia.js and React 19 to render dynamic UI components without building a separate API.

### 2.2 User Classes & Characteristics

* **Authenticated Developer / Owner:** Full CRUD control over projects, tickets, and associated journal entries. Focuses on speed, keyboard navigation, and historical code context.

### 2.3 Operating Environment

* **Local Environment:** Laravel Herd (Windows/macOS), PHP 8.4+, Node.js v22/v26, Bun.
* **Database:** MySQL 8.0+.
* **Browser:** Modern evergreen browsers (Chrome, Firefox, Edge, Safari).

---

## 3. System Features & Functional Requirements

### 3.1 Project Management

* **REQ-1.1 (Create Project):** The system shall allow users to create a project specifying a `name`, unique auto-generated `slug`, and an optional `description`.
* **REQ-1.2 (Project Listing):** The dashboard shall display a structured list of all active projects with quick indicators of open ticket counts.

### 3.2 Ticket & Issue Tracking

* **REQ-2.1 (Create Ticket):** Users shall be able to create tickets linked to a specific project with a `title`, `description`, `status` (`backlog`, `in_progress`, `done`), and `priority` (`low`, `normal`, `high`, `urgent`).
* **REQ-2.2 (State Transition):** Users shall be able to update ticket statuses dynamically with immediate UI feedback via Inertia page props.

### 3.3 Embedded Developer Journal (The Ticket Log)

* **REQ-3.1 (Append Journal Entry):** Each ticket shall support a collection of chronological log entries (`ticket_logs`).
* **REQ-3.2 (Rich Text / Markdown Support):** Journal entries shall accept Markdown text to record architectural decisions, code snippets, blockers, and solutions.
* **REQ-3.3 (Audit Traceability):** The system shall permanently associate timestamps with each log entry to ensure long-term historical tracking of decisions made during development.

---

## 4. Non-Functional Requirements

### 4.1 Performance

* **NFR-1.1:** Page transitions mediated via Inertia.js shall render in under **300ms** under local development parameters.
* **NFR-1.2:** Database queries for project dashboards must execute efficiently using proper indexing on `project_id` and `status` fields.

### 4.2 Security & Authentication

* **NFR-2.1:** Authentication shall rely on secure, session-based cookies via Laravel Breeze (`auth.user`).
* **NFR-2.2:** All database write operations must enforce strict Eloquent mass-assignment protection and form request validation.

### 4.3 Maintainability & Code Standards

* **NFR-3.1:** Backend architecture must follow strict PHP type-hinting, strict return types, and clean controller action methods.
* **NFR-3.2:** Frontend components must be modularly structured inside React with clean prop typing.

---
