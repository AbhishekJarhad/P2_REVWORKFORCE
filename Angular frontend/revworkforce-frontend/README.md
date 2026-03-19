# RevWorkforce HRM — Angular Frontend

A complete Angular 17 frontend for the RevWorkforce Spring Boot backend.

## Tech Stack
- **Angular 17** — Standalone components, signals, inject()
- **JWT Auth** — HTTP interceptor + localStorage
- **Role-based routing** — ADMIN / MANAGER / EMPLOYEE
- **Base URL** — `http://localhost:8080/api`

---

## Project Structure

```
src/app/
├── core/
│   ├── models/          # TypeScript interfaces (match Java DTOs)
│   ├── services/
│   │   ├── auth.service.ts      # Login, logout, token, role helpers
│   │   └── api.service.ts       # All API calls (Employee, Leave, Performance, Admin)
│   ├── interceptors/
│   │   └── auth.interceptor.ts  # Adds Bearer token to every request
│   └── guards/
│       └── auth.guard.ts        # Route protection + role guard
├── features/
│   ├── auth/login/              # Login page
│   ├── dashboard/               # Role-aware dashboard
│   ├── employees/
│   │   ├── profile/             # My Profile + edit
│   │   └── list/                # Employee list (ADMIN/MANAGER)
│   ├── leaves/                  # Apply, view, approve/reject leaves
│   ├── performance/             # Self-reviews + manager feedback
│   ├── goals/                   # Goal tracking with progress
│   └── admin/                   # Admin panel (quotas, reset balances)
└── shared/
    └── components/shell/        # Sidebar + layout shell
```

---

## Setup & Run

### Prerequisites
- Node.js 18+
- Angular CLI: `npm install -g @angular/cli`
- Backend running on `http://localhost:8080`

### Install & Start
```bash
npm install
ng serve
```

Open `http://localhost:4200`

---

## Features by Role

### All Roles
- Login / Logout
- Dashboard with leave balance, recent requests, active goals
- My Profile — view & edit personal info
- Apply for Leave (Casual / Sick / Paid)
- View leave history
- Create & submit performance self-reviews
- Set and track goals with progress %

### Manager + Admin
- View team members
- Approve / Reject team leave requests
- Review pending team performance reviews
- Add manager feedback and star rating
- View all team performance reviews

### Admin Only
- Create new employees
- Assign managers to employees
- Toggle employee active/inactive status
- Configure leave quotas per type/year
- Reset leave balances for new year
- Full admin dashboard stats

---

## API Endpoints Used

| Service | Endpoints |
|---|---|
| Auth | `POST /api/auth/login` |
| Employee | `GET/PUT /api/employees/me`, `GET /api/employees`, `GET /api/employees/my-team` |
| Leave | `GET /api/leaves/balance`, `POST /api/leaves/apply`, `GET /api/leaves/my-leaves`, `PUT /api/leaves/{id}/cancel`, `GET /api/leaves/team`, `PUT /api/leaves/{id}/process`, `GET /api/leaves/all` |
| Performance | `POST/PUT /api/performance/reviews`, `PUT /api/performance/reviews/{id}/submit`, `PUT /api/performance/reviews/{id}/feedback`, `GET /api/performance/reviews/my`, `GET /api/performance/reviews/team` |
| Goals | `POST/PUT/DELETE /api/performance/goals`, `GET /api/performance/goals/my` |
| Admin | `GET /api/admin/dashboard`, `POST /api/admin/employees`, `PUT /api/admin/employees/{id}/assign-manager/{mId}`, `PUT /api/admin/employees/{id}/toggle-status`, `POST/GET /api/admin/leave-quotas`, `POST /api/admin/reset-leave-balances/{year}` |

---

## Test Credentials

| Role | Email | Password |
|---|---|---|
| Admin | admin@revworkforce.com | admin123 |
| Manager | manager@revworkforce.com | manager123 |
| Employee | employee@revworkforce.com | employee123 |

> Quick-fill buttons are available on the login screen!

---

## Design System
- Dark theme — deep navy/black backgrounds
- **Syne** display font + **DM Sans** body font
- CSS custom properties for all colors/spacing
- Responsive — collapses to single column on mobile
- Collapsible sidebar
