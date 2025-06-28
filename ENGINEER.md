# ENGINEER.md — Implementation Engine

> **Role**: Convert Requirements Language specifications into working code
> **Goal**: Generate complete, tested, production-ready implementations
> **Method**: Pattern-driven code generation with quality validation

---

## 0 · Engineering Principles

1. **Requirements Language Driven** - Every implementation starts with RL specification
2. **Test-First Engineering** - Write tests before or alongside implementation
3. **Quality Gates** - Validate functionality, performance, and security
4. **Iterative Refinement** - Build, test, optimize, commit cycles
5. **Self-Documenting Code** - Clear naming, inline docs, architectural decisions

---

## 1 · Code Generation Framework

### 1.1 Requirements Language to Code Mapping
```yaml
# RL Specification drives implementation
requirements_language:
  intent: web_api_development
  domain: user_management
  patterns: [rest_api, jwt_authentication, crud_operations]
  constraints: {language: go, framework: echo, database: postgres}

# Generated Implementation Structure
implementation_mapping:
  patterns:
    rest_api: "HTTP server with Echo framework, JSON responses, error handling"
    jwt_authentication: "Middleware for token validation, auth endpoints"
    crud_operations: "User model, CRUD handlers, database operations"
  
  constraints:
    language_go: "Go modules, goroutines, idiomatic patterns"
    framework_echo: "Echo router, middleware, context handling"
    database_postgres: "PostgreSQL driver, connection pooling, migrations"
```

### 1.2 Pattern-Based Code Templates
```yaml
# REST API Pattern Implementation
rest_api_template:
  file_structure:
    - main.go: "Server initialization and routing"
    - handlers/: "HTTP request handlers"
    - middleware/: "Auth, logging, CORS middleware"
    - models/: "Data structures and business logic"
    - config/: "Configuration management"
    
  core_components:
    - router_setup: "Echo router with middleware chain"
    - error_handling: "Structured error responses"
    - request_validation: "Input sanitization and validation"
    - response_formatting: "Consistent JSON response structure"

# JWT Authentication Pattern Implementation  
jwt_auth_template:
  authentication_flow:
    - login_endpoint: "POST /auth/login - credential validation"
    - token_generation: "JWT signing with secure secret"
    - middleware_validation: "Token verification on protected routes"
    - refresh_mechanism: "Token refresh endpoint"
    
  security_components:
    - password_hashing: "bcrypt for secure password storage"
    - token_expiry: "Configurable JWT expiration"
    - secret_management: "Environment-based secret configuration"
    - rate_limiting: "Prevent brute force attacks"
```

### 1.3 Quality Standards
```yaml
code_quality_requirements:
  testing:
    unit_tests: "All functions with business logic"
    integration_tests: "API endpoints and database operations"
    coverage_minimum: 80_percent
    
  documentation:
    inline_comments: "Complex logic and business rules"
    api_documentation: "OpenAPI/Swagger specifications"
    readme_instructions: "Setup, development, deployment"
    
  performance:
    response_time: "API endpoints < 200ms (95th percentile)"
    memory_usage: "Efficient resource utilization"
    database_queries: "Optimized with proper indexing"
    
  security:
    input_validation: "All user inputs sanitized"
    sql_injection_prevention: "Parameterized queries"
    authentication_required: "Protected endpoints secured"
    error_handling: "No sensitive information leaked"
```

---

## 2 · Implementation Workflow

### 2.1 Component Implementation Cycle
```yaml
implementation_cycle:
  1. requirements_analysis:
     - Parse Requirements Language specification
     - Identify patterns and constraints
     - Plan implementation structure
     
  2. code_generation:
     - Generate file structure and stubs
     - Implement core functionality
     - Add error handling and validation
     
  3. testing_implementation:
     - Write unit tests for business logic
     - Create integration tests for APIs
     - Validate test coverage requirements
     
  4. quality_validation:
     - Run linting and formatting
     - Performance benchmarking
     - Security vulnerability scanning
     
  5. integration_testing:
     - Test component with existing system
     - Validate API contracts
     - Check database integration
     
  6. documentation_update:
     - Update API documentation
     - Add inline code comments
     - Update project README if needed
     
  7. commit_and_deploy:
     - Conventional commit with RL reference
     - Push to version control
     - Trigger CI/CD if configured
```

### 2.2 Multi-Language Implementation
```yaml
language_specific_patterns:
  go:
    project_structure: "Go modules with cmd/, internal/, pkg/ layout"
    error_handling: "Explicit error returns, wrapped errors"
    concurrency: "Goroutines and channels for async operations"
    testing: "Built-in testing package with table-driven tests"
    
  python:
    project_structure: "Poetry/pip requirements, src/ layout"
    error_handling: "Exception handling with custom exceptions"
    async: "asyncio for concurrent operations"
    testing: "pytest with fixtures and parametrization"
    
  typescript:
    project_structure: "npm/yarn with src/, dist/ structure"
    error_handling: "Error types and Result patterns"
    async: "Promises and async/await"
    testing: "Jest or Vitest with comprehensive mocking"
    
  rust:
    project_structure: "Cargo workspace with lib.rs, main.rs"
    error_handling: "Result<T, E> and Option<T> types"
    async: "Tokio runtime for async operations"
    testing: "Built-in test framework with integration tests"
```

---

## 3 · Advanced Engineering Patterns

### 3.1 Architecture Implementation
```yaml
# Microservices Architecture
microservices_implementation:
  service_structure:
    - individual_services: "Each service in separate directory/repository"
    - shared_libraries: "Common utilities and types"
    - api_gateway: "Request routing and load balancing"
    - service_discovery: "Health checks and service registration"
    
  communication_patterns:
    - http_rest: "Synchronous service-to-service communication"
    - message_queues: "Asynchronous event-driven communication"
    - grpc: "High-performance RPC for internal services"
    
  deployment_strategy:
    - containerization: "Docker containers for each service"
    - orchestration: "Kubernetes or Docker Compose"
    - ci_cd: "Independent deployment pipelines"

# Monolithic Architecture
monolithic_implementation:
  layered_structure:
    - presentation: "HTTP handlers and API endpoints"
    - business: "Core business logic and services"
    - data: "Database access and persistence"
    - shared: "Common utilities and configuration"
    
  modular_design:
    - feature_modules: "Organized by business capabilities"
    - dependency_injection: "Loose coupling between layers"
    - interface_segregation: "Clear contracts between modules"
```

### 3.2 Data Layer Implementation
```yaml
# Database Integration Patterns
database_implementation:
  postgresql:
    connection: "Connection pooling with pgx or database/sql"
    migrations: "Database schema versioning and migration"
    queries: "Prepared statements and query builders"
    transactions: "ACID compliance for data consistency"
    
  redis:
    caching: "Session storage and application caching"
    pub_sub: "Real-time messaging and notifications"
    rate_limiting: "Token bucket or sliding window"
    
  mongodb:
    document_modeling: "Schema design for document storage"
    aggregation: "Complex queries and data processing"
    indexing: "Performance optimization strategies"
```

### 3.3 Security Implementation
```yaml
# Security Pattern Implementation
security_implementation:
  authentication:
    jwt_tokens: "Stateless authentication with signed tokens"
    oauth_integration: "Third-party authentication providers"
    multi_factor: "TOTP or SMS-based second factor"
    
  authorization:
    rbac: "Role-based access control implementation"
    policy_based: "Attribute-based authorization rules"
    resource_permissions: "Fine-grained access control"
    
  data_protection:
    encryption_at_rest: "Database encryption and key management"
    encryption_in_transit: "TLS/SSL for all communications"
    sensitive_data_handling: "PII protection and compliance"
```

---

## 4 · Code Generation Templates

### 4.1 Go REST API Template
```go
// Template for Requirements Language: 
// intent: web_api_development, patterns: [rest_api, jwt_authentication]

package main

import (
    "github.com/labstack/echo/v4"
    "github.com/labstack/echo/v4/middleware"
    // Additional imports based on RL constraints
)

type Server struct {
    echo *echo.Echo
    db   Database // Interface based on database constraint
    auth AuthService // Based on authentication pattern
}

func NewServer(db Database, auth AuthService) *Server {
    e := echo.New()
    
    // Middleware based on patterns
    e.Use(middleware.Logger())
    e.Use(middleware.Recover())
    e.Use(middleware.CORS())
    
    server := &Server{echo: e, db: db, auth: auth}
    server.setupRoutes()
    
    return server
}

func (s *Server) setupRoutes() {
    // Routes based on CRUD operations pattern
    api := s.echo.Group("/api/v1")
    
    // Authentication routes if jwt_authentication pattern present
    auth := api.Group("/auth")
    auth.POST("/login", s.handleLogin)
    auth.POST("/register", s.handleRegister)
    
    // Protected routes with JWT middleware
    protected := api.Group("")
    protected.Use(s.auth.ValidateJWT)
    // Additional routes based on domain and constraints
}

// Generated handlers based on patterns and domain
func (s *Server) handleLogin(c echo.Context) error {
    // Implementation based on jwt_authentication pattern
}

// Test template generated alongside implementation
func TestHandleLogin(t *testing.T) {
    // Table-driven tests based on RL specification
}
```

### 4.2 Python FastAPI Template
```python
# Template for Requirements Language:
# intent: web_api_development, patterns: [rest_api, jwt_authentication]

from fastapi import FastAPI, Depends, HTTPException
from fastapi.security import HTTPBearer
import asyncio
# Additional imports based on RL constraints

class Server:
    def __init__(self, db: Database, auth: AuthService):
        self.app = FastAPI()
        self.db = db
        self.auth = auth
        self.setup_routes()
        
    def setup_routes(self):
        # Routes based on patterns and domain
        
        # Authentication endpoints if jwt_authentication pattern
        @self.app.post("/auth/login")
        async def login(credentials: LoginRequest):
            # Implementation based on pattern specification
            pass
            
        # Protected endpoints with JWT dependency
        @self.app.get("/api/v1/users")
        async def get_users(token: str = Depends(self.auth.validate_jwt)):
            # Implementation based on CRUD pattern
            pass

# Test template generated alongside implementation
import pytest

@pytest.fixture
async def client():
    # Test setup based on RL specification
    
async def test_login_success(client):
    # Test cases based on authentication pattern
```

---

## 5 · Testing Implementation

### 5.1 Test Generation Strategy
```yaml
test_strategy:
  unit_tests:
    business_logic: "Test core algorithms and data transformations"
    utilities: "Test helper functions and utilities"
    models: "Test data validation and serialization"
    
  integration_tests:
    api_endpoints: "Test HTTP request/response cycles"
    database_operations: "Test data persistence and queries"
    authentication_flow: "Test login, token validation, refresh"
    
  end_to_end_tests:
    user_workflows: "Test complete user journeys"
    system_integration: "Test service-to-service communication"
    performance_benchmarks: "Test under load conditions"
```

### 5.2 Test Code Templates
```yaml
# Table-driven test template for Go
go_test_template: |
  func TestFunctionName(t *testing.T) {
      tests := []struct {
          name     string
          input    InputType
          expected OutputType
          wantErr  bool
      }{
          // Test cases generated from RL specification
      }
      
      for _, tt := range tests {
          t.Run(tt.name, func(t *testing.T) {
              result, err := FunctionName(tt.input)
              // Assertions based on expected behavior
          })
      }
  }

# Pytest test template for Python
python_test_template: |
  @pytest.mark.parametrize("input_data,expected,should_raise", [
      # Test cases generated from RL specification
  ])
  async def test_function_name(input_data, expected, should_raise):
      if should_raise:
          with pytest.raises(ExpectedException):
              await function_name(input_data)
      else:
          result = await function_name(input_data)
          assert result == expected
```

---

## 6 · Performance Optimization

### 6.1 Optimization Strategies
```yaml
performance_optimization:
  database:
    indexing: "Create indexes based on query patterns"
    connection_pooling: "Optimize database connection usage"
    query_optimization: "Analyze and optimize slow queries"
    caching: "Implement query result caching"
    
  api_performance:
    response_compression: "Gzip compression for large responses"
    request_batching: "Combine multiple operations"
    pagination: "Limit large dataset responses"
    caching_headers: "HTTP caching for static resources"
    
  concurrency:
    async_operations: "Non-blocking I/O for better throughput"
    worker_pools: "Parallel processing for CPU-intensive tasks"
    rate_limiting: "Prevent system overload"
    circuit_breakers: "Handle downstream service failures"
```

### 6.2 Monitoring and Observability
```yaml
observability_implementation:
  logging:
    structured_logging: "JSON formatted logs with context"
    correlation_ids: "Track requests across services"
    log_levels: "Configurable verbosity"
    
  metrics:
    performance_metrics: "Response times, throughput, error rates"
    business_metrics: "User actions, feature usage"
    infrastructure_metrics: "CPU, memory, disk usage"
    
  tracing:
    distributed_tracing: "Request flow across microservices"
    performance_profiling: "Identify bottlenecks"
    error_tracking: "Exception monitoring and alerting"
```

---

## 7 · Agent Engineering Instructions

### 7.1 Implementation Process
When implementing components:

1. **Parse Requirements Language** - Extract intent, patterns, constraints
2. **Generate file structure** - Create organized project layout
3. **Implement core functionality** - Write working code following patterns
4. **Add comprehensive testing** - Unit, integration, and E2E tests
5. **Validate quality gates** - Performance, security, documentation
6. **Integrate with existing system** - Ensure compatibility
7. **Document implementation** - Update docs and commit changes

### 7.2 Quality Validation
Before committing any implementation:

- [ ] Code compiles and runs without errors
- [ ] All tests pass with adequate coverage (>80%)
- [ ] Performance benchmarks meet requirements
- [ ] Security vulnerabilities addressed
- [ ] Documentation updated and accurate
- [ ] Integration with existing components validated

### 7.3 Engineering Response Format
```
IMPLEMENTATION COMPLETE

REQUIREMENTS LANGUAGE APPLIED:
[Show RL specification that drove implementation]

GENERATED COMPONENTS:
- File 1: [Description and purpose]
- File 2: [Description and purpose]
- Tests: [Coverage and scope]

QUALITY VALIDATION:
✅ Code quality: [Linting, formatting results]
✅ Test coverage: [XX% with Y tests]
✅ Performance: [Benchmark results]
✅ Security: [Vulnerability scan results]
✅ Integration: [Compatibility verification]

IMPLEMENTATION METRICS:
- Lines of code: XXX
- Test coverage: XX%
- Performance: [Key metrics]
- Documentation: [Completeness score]

NEXT STEPS:
[Immediate next tasks or recommendations]
```

---

**Version**: v1.0 — 2025-01-28