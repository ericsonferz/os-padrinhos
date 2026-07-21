# Os Padrinhos — API Boundaries

## Objetivo

Definir fronteiras entre módulos e futuras APIs.

---

# Planning Context

Responsável por:

- WeddingProject
- WeddingEvent
- WeddingStage
- Needs

---

Endpoints futuros:

POST

/projects


GET

/projects/{id}


POST

/projects/{id}/events


POST

/events/{id}/stages


---

# Budget Context

Responsável por:

- Budget
- BudgetItems
- Estimates

Endpoints:

GET

/stages/{id}/budget


POST

/budget-items

---

# Marketplace Context

Responsável por:

- Vendors
- VendorServices
- Categories

Endpoints:

GET

/vendors

GET

/services


---

# Booking Context

Responsável por:

- Contratações
- Serviços reservados

Endpoints:

POST

/bookings


GET

/bookings/{id}


---

# Execution Context

Responsável por:

- Tasks
- Checklist
- Timeline

Endpoints:

POST

/tasks

PATCH

/tasks/{id}

---

# Analytics Context

Responsável por:

- métricas
- custos médios
- tendências