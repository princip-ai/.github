### **1. General Rules**
- Use **UPPER_SNAKE_CASE** for all environment variable names.
- Use **descriptive names** that clearly indicate the purpose of the variable.
- Group related variables under a **common prefix** (e.g., `DB_`, `REDIS_`, `LOG_`).
- Avoid **redundant prefixes** or suffixes unless necessary for clarity.
- Use **consistent terminology** across all variables (e.g., `ENABLED` instead of `USE_` or `IS_`).

---

### **2. Naming Pattern**
The general pattern for naming environment variables is:

```
<GROUP>_<SUBGROUP>_<DESCRIPTIVE_NAME>
```

- **`<GROUP>`**: Represents the high-level category or module the variable belongs to (e.g., `APP`, `DB`, `LOG`, `REDIS`).
- **`<SUBGROUP>`**: (Optional) Represents a subcategory within the group (e.g., `DATABASE_LOGGING` → `DB_LOG_LEVEL`).
- **`<DESCRIPTIVE_NAME>`**: Describes the specific purpose of the variable (e.g., `HOST`, `PORT`, `ENABLED`).

---

### **3. Examples of Groups and Subgroups**

#### **Application Configuration**
- Prefix: `APP_`
- Examples:
  - `APP_NAME`
  - `APP_PORT`
  - `APP_ENV` (e.g., `production`, `development`)
  - `APP_VERSION`

#### **Database Configuration**
- Prefix: `DB_`
- Examples:
  - `DB_TYPE` (e.g., `postgres`, `mysql`)
  - `DB_HOST`
  - `DB_PORT`
  - `DB_USERNAME`
  - `DB_PASSWORD`
  - `DB_NAME`
  - `DB_SCHEMA`
  - `DB_LOGGING` (boolean)

#### **Redis Configuration**
- Prefix: `REDIS_`
- Examples:
  - `REDIS_ENABLED` (boolean)
  - `REDIS_HOST`
  - `REDIS_PORT`
  - `REDIS_PASSWORD`

#### **Logging Configuration**
- Prefix: `LOG_`
- Examples:
  - `LOG_LEVEL` (e.g., `info`, `debug`)
  - `LOG_PRETTIER_FORMAT` (boolean)
  - `LOG_USE_DATE_CONTEXT_PREFIX` (boolean)

#### **Event Bus Configuration**
- Prefix: `EVENT_BUS_`
- Examples:
  - `EVENT_BUS_ENABLED` (boolean)
  - `EVENT_BUS_SERVER`
  - `EVENT_BUS_DEBUG_MODE` (boolean)
  - `EVENT_BUS_AUTH_TOKEN`

#### **Throttling Configuration**
- Prefix: `THROTTLING_`
- Examples:
  - `THROTTLING_ENABLED` (boolean)
  - `THROTTLING_TTL` (time-to-live in milliseconds)
  - `THROTTLING_LIMIT` (maximum number of requests)

#### **Request Configuration**
- Prefix: `REQUEST_`
- Examples:
  - `REQUEST_SIZE_LIMIT_ENABLED` (boolean)
  - `REQUEST_SIZE_LIMIT` (e.g., `50mb`)

#### **Error Handling Configuration**
- Prefix: `ERROR_`
- Examples:
  - `ERROR_EMAIL_SENDING_ENABLED` (boolean)
  - `ERROR_EMAIL_SENDING_FREQUENCY` (milliseconds)

#### **Security Configuration**
- Prefix: `SECURITY_`
- Examples:
  - `SECURITY_OBFUSCATOR_ENABLED` (boolean)
  - `SECURITY_JWT_SECRET`

#### **Microservices Configuration**
- Prefix: `MICROSERVICE_`
- Examples:
  - `MICROSERVICE_URL`

#### **Company Configuration**
- Prefix: `COMPANY_`
- Examples:
  - `COMPANY_NAME`
  - `COMPANY_ADDRESS`

#### **Miscellaneous**
- Prefix: (No prefix, or use `MISC_` if needed)
- Examples:
  - `COMMIT_HASH`
  - `SERVICE_TIMEOUT`

---

### **4. Boolean Variables**
For boolean variables, use the suffix `_ENABLED` or `_DISABLED` to make the purpose clear:
- `REDIS_ENABLED`
- `DB_LOGGING_ENABLED`
- `THROTTLING_ENABLED`

---

### **5. Special Cases**
- **Timeouts**: Use the suffix `_TIMEOUT` and specify the value in milliseconds.
  - Example: `EVENT_BUS_CONNECTION_TIMEOUT=60000`
- **Limits**: Use the suffix `_LIMIT` and specify the value with units (e.g., `50mb`, `1000`).
  - Example: `REQUEST_SIZE_LIMIT=50mb`
- **Frequencies**: Use the suffix `_FREQUENCY` and specify the value in milliseconds.
  - Example: `ERROR_EMAIL_SENDING_FREQUENCY=60000`

---

### **6. Example of Refactored Environment Variables**

Here’s how your environment variables would look after applying this pattern:

```env
# Application
APP_NAME=auth-service
APP_PORT=15500
APP_ENV=production
APP_TYPE=api
APP_VERSION=1.0.0

# Database
DB_TYPE=postgres
DB_HOST=127.0.0.1
DB_PORT=5432
DB_USERNAME=admin
DB_PASSWORD=admin
DB_NAME=postgres
DB_SCHEMA=auth
DB_REPLICA_SET=rs0
DB_LOGGING=true
DB_AUTH_SOURCE=admin

# Redis
REDIS_ENABLED=false
REDIS_HOST=127.0.0.1
REDIS_PORT=6379

# Logging
LOG_LEVEL=info
LOG_PRETTIER_FORMAT=true
LOG_USE_DATE_CONTEXT_PREFIX=true

# Event Bus
EVENT_BUS_ENABLED=true
EVENT_BUS_SERVER=nats://127.0.0.1:4222
EVENT_BUS_DEBUG_MODE=true
EVENT_BUS_AUTH_TOKEN=NLpvMWxpot
EVENT_BUS_CONNECTION_TIMEOUT=60000

# Throttling
THROTTLING_ENABLED=false
THROTTLING_TTL=1000
THROTTLING_LIMIT=50000

# Request
REQUEST_SIZE_LIMIT_ENABLED=false
REQUEST_SIZE_LIMIT=50mb

# Error Handling
ERROR_EMAIL_SENDING_ENABLED=false
ERROR_EMAIL_SENDING_FREQUENCY=60000

# Security
SECURITY_OBFUSCATOR_ENABLED=false

# External Services
MICROSERVICE_AUTH_SERVICE_URL=https://api.github.com

# Company
COMPANY_NAME=aspen

# Miscellaneous
COMMIT_HASH=latest
SERVICE_TIMEOUT=30000
```

---

### **7. Benefits of This Pattern**

1. **Consistency**:
   - All variables follow the same structure, making them easier to read and understand.

2. **Scalability**:
   - Adding new variables is straightforward because the naming convention is clear.

3. **Grouping**:
   - Related variables are grouped under a common prefix, making it easier to manage and update them.

4. **Readability**:
   - Descriptive names make it clear what each variable is used for.

5. **Maintainability**:
   - Reduces the risk of errors when referencing variables in code.

---

### **Final Thoughts**

This naming convention pattern ensures that your environment variables are **consistent**, **descriptive**, and **easy to manage**. By following this structure, you’ll create a clean and scalable configuration system for your application.