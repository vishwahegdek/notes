## 🧱 PostgreSQL Architecture (Simplified)

### 🔑 Key Concepts:

#### 1. Cluster
- A *PostgreSQL cluster* is a collection of databases managed by a single server instance (`postgres` process)
- Usually initialized at `/var/lib/postgresql/<version>/main` on Ubuntu systems

#### 2. Database
- A cluster can host **multiple databases** (like `template1`, `postgres`, and your own)
- You connect to **one database at a time**

#### 3. Roles (Users and Groups)
- PostgreSQL uses **roles** to manage authentication and authorization
- A role can **login**, **own databases**, and have **privileges**
- You can have:
  - **Login roles** (users): `CREATE ROLE vishwa LOGIN;`
  - **Group roles**: Roles without LOGIN that act like groups

#### 4. Schemas
- A schema is a **namespace inside a database** that contains tables, views, functions, etc.
- Default schema: `public`

#### 5. Processes
- `postmaster` is the master process that manages:
  - **Client connections**
  - **Autovacuum**
  - **Background writers**
  - **WAL writers** (for transaction logs)