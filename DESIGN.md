# Security Design Document

## Authentication and Authorization Quality Attributes

### 1. Authentication

**Definition**: The process of verifying the identity of a user or system.

**Implementation**:
- Form-based login with username and password
- BCrypt password encoding for secure password storage
- Session-based authentication using Spring Security
- Login failure handling with error messages

**Security Measures**:
- Passwords are hashed using BCrypt before storage
- Session management prevents unauthorized access
- Login attempts are validated against stored user credentials
- Failed login attempts display appropriate error messages

### 2. Authorization

**Definition**: The process of determining what resources a user can access and what actions they can perform.

**Implementation**:
- Role-based access control (RBAC)
- Two user roles: ADMIN and USER
- URL-based authorization using Spring Security
- Method-level access control

**Access Control Rules**:
- `/` and `/login` - Accessible to all users
- `/admin/**` - Accessible only to users with ADMIN role
- `/user/**` - Accessible to users with USER or ADMIN roles
- `/dashboard` - Accessible to all authenticated users

### 3. Security Quality Attributes

#### Confidentiality
- User passwords are encrypted using BCrypt
- Session data is protected
- Sensitive pages require authentication

#### Integrity
- User credentials are validated before access
- Role-based permissions prevent unauthorized modifications
- CSRF protection is implemented

#### Availability
- Simple in-memory user storage for demonstration
- Basic error handling for failed authentication
- Session timeout management

#### Accountability
- User sessions track authenticated users
- Role-based access provides audit trail capabilities

### 4. Security Architecture

**Components**:
- **SecurityConfig**: Configures authentication and authorization rules
- **AuthController**: Handles login, logout, and page routing
- **UserDetailsService**: Manages user credentials and roles
- **PasswordEncoder**: Handles password encryption

**Security Flow**:
1. User attempts to access protected resource
2. Spring Security intercepts request
3. If not authenticated, redirects to login page
4. User submits credentials
5. System validates credentials against stored users
6. If valid, creates authenticated session
7. Authorizes access based on user roles
8. Grants or denies access to requested resource

### 5. Limitations

- In-memory user storage (not persistent)
- Simple password policy
- Basic session management
- No password reset functionality
- No account lockout mechanism

### 6. Testing

**Test Users**:
- Admin: username=`admin`, password=`admin`, role=`ADMIN`
- User: username=`user`, password=`user`, role=`USER`

**Test Scenarios**:
- Valid login with admin credentials
- Valid login with user credentials
- Invalid login attempts
- Access to admin-only pages
- Access to user pages
- Logout functionality