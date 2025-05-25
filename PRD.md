# 📝 Product Requirements Document (PRD)

## 1. 📘 Product Overview
**Product Name:**  
**Date:**  
**Owner:**  
**Stakeholders:**  
**Purpose:**  
_Describe what this product is and the business problem it solves._

---

## 2. 📚 Ontology

_This section defines the entities (data objects), attributes, and relationships between them. It serves as a semantic map for both technical and compliance design._

### 2.1 Entities & Attributes

| Entity   | Attributes                                         | Notes                        |
|----------|----------------------------------------------------|------------------------------|
| User     | id, name, email, password, role, created_at        | RBAC requires `role`         |
| Project  | id, title, description, owner_id, status           | Owner is a User              |
| Task     | id, title, status, assignee_id, project_id         | FK to User and Project       |
| Comment  | id, body, task_id, author_id, created_at           | FK to Task and User          |

### 2.2 Relationships

- A **User** can have multiple **Projects**
- A **Project** can have multiple **Tasks**
- A **Task** can have multiple **Comments**
- A **User** can be assigned to multiple **Tasks**

---

## 3. 👥 Roles and Features

_Defines what each role can do in the system._

| Role          | Description                          | Features Available                         |
|---------------|--------------------------------------|--------------------------------------------|
| Admin         | Full access to all data              | User management, project oversight         |
| Project Owner | Manages specific projects            | Create/edit projects, assign tasks         |
| Contributor   | Works on tasks                       | View assigned tasks, update status         |
| Viewer        | Read-only access                     | View dashboards and project status         |

---

## 4. 🔧 Features

_List of features grouped by domain/module._

### 4.1 User Management
- User registration and authentication
- Role assignment and permission control
- Profile management

### 4.2 Project Management
- Create/edit/delete projects
- Add/remove contributors
- Project status tracking

### 4.3 Task Management
- Create/edit/delete tasks
- Assign tasks to users
- Update task status
- Add task comments

### 4.4 Audit & Logs (for compliance)
- View change logs per user/entity
- Export logs for compliance reports

---

## 5. 🧩 User Stories (per Role)

_These are detailed stories that derive from the features._

### 5.1 Admin

- **US001**: As an Admin, I want to create and manage users so that I can control access across the system.
- **US002**: As an Admin, I want to see audit logs so that I can monitor user activity for compliance.
- **US003**: As an Admin, I want to assign roles to users so I can manage permissions.

### 5.2 Project Owner

- **US004**: As a Project Owner, I want to create a new project so I can track its progress.
- **US005**: As a Project Owner, I want to assign contributors to tasks so the work is delegated.
- **US006**: As a Project Owner, I want to change project status to reflect milestones.

### 5.3 Contributor

- **US007**: As a Contributor, I want to view my assigned tasks so I can manage my workload.
- **US008**: As a Contributor, I want to update the task status to indicate progress.
- **US009**: As a Contributor, I want to comment on tasks for collaboration.

### 5.4 Viewer

- **US010**: As a Viewer, I want to see the project status dashboard so I can stay informed.
- **US011**: As a Viewer, I want to read task details so I understand team activities.

---

## 6. ✅ Acceptance Criteria

_Each user story should link to specific acceptance tests._

### Example for US004:
- [ ] Can create a project with title and description
- [ ] Project shows under “My Projects”
- [ ] Only the creator has edit/delete rights

---

## 7. 🔐 Compliance Considerations

- Role-based data access enforcement
- Data encryption at rest and in transit
- Audit trails for user actions
- GDPR/PDPA-compliant user data deletion
