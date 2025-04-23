# PostgreSQL Login and Architecture Notes

## 🔐 Logging into PostgreSQL (as `postgres` user)

PostgreSQL creates a default *Linux* user called `postgres` during installation. This user also has a matching PostgreSQL role (`postgres`).

### ✅ Login without PostgreSQL password:

1. **Switch to the `postgres` Linux user**:
   ```bash
   sudo -i -u postgres
   ```

2. **Access the PostgreSQL shell (`psql`) directly**:
   ```bash
   psql
   ```

   You should now see the PostgreSQL prompt:
   ```
   postgres=#
   ```

3. **Exit `psql`**:
   ```sql
   \q
   ```

> 🔹 This method works because of Unix domain socket authentication (`peer` auth), which doesn't require a PostgreSQL password if you're logged in as the correct Linux user (`postgres`).
      If not working do this
  ```bash
  sudo nano /etc/postgresql/14/main/pg_hba.conf
  ```
  Look at this section
  ```sql
  # "local" is for Unix domain socket connections only
  local   all             postgres                                md5
  ```
  change the md5 to peer 
  Then
  ```bash
  sudo systemctl restart postgresql
  ```
  
  Then It should Work
  Use this to reset password
  ```sql
  ALTER USER postgres PASSWORD 'new_password_here';
  ```

### 🔐 Peer vs. MD5 Authentication in PostgreSQL

| Feature                     | **Peer Authentication**                          | **MD5 Authentication**                          |
|----------------------------|--------------------------------------------------|-------------------------------------------------|
| **Authentication Type**    | Based on matching OS username to PostgreSQL role | Based on username and password hash             |
| **Password Required**      | ❌ No password required                          | ✅ Password required                             |
| **Default for Local?**     | ✅ Yes                                           | ❌ No                                            |
| **Security**               | Safer for trusted local users (no password handling) | Requires password management (less secure if mishandled) |
| **Use Case**               | Local connections on trusted systems             | Remote connections or when OS and DB users differ |
