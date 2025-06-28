# PATTERNS.md — Solution Template Library

> **Role**: Provide reusable solution templates for Requirements Language compilation
> **Goal**: Enable pattern-based optimization and rapid template application
> **Method**: Hierarchical pattern inheritance with constraint propagation

---

## 0 · Pattern System Principles

1. **Inheritance** - Patterns can extend and compose other patterns
2. **Constraint Propagation** - Patterns imply technical requirements automatically
3. **Template Matching** - Keywords trigger appropriate pattern selection
4. **Composition** - Multiple patterns combine for complex solutions

---

## 1 · Core Pattern Categories

### 1.1 Web Development Patterns
| Pattern | Purpose | Implied Constraints |
|---------|---------|-------------------|
| `rest_api` | RESTful web services | HTTP methods, JSON, status codes |
| `graphql_api` | GraphQL endpoints | Schema, resolvers, type system |
| `websocket_api` | Real-time communication | Persistent connections, events |
| `spa_application` | Single-page apps | Client routing, state management |
| `jwt_authentication` | Token-based auth | JWT middleware, refresh tokens |
| `oauth_integration` | Third-party auth | OAuth flow, provider integration |

### 1.2 Data Processing Patterns
| Pattern | Purpose | Implied Constraints |
|---------|---------|-------------------|
| `etl_pipeline` | Extract-Transform-Load | Data sources, transformation, storage |
| `stream_processing` | Real-time data streams | Event handling, buffer management |
| `batch_processing` | Large dataset processing | Chunking, parallel execution |
| `ml_inference` | Machine learning | Model loading, prediction API |
| `data_validation` | Quality assurance | Schema validation, error handling |

### 1.3 Infrastructure Patterns
| Pattern | Purpose | Implied Constraints |
|---------|---------|-------------------|
| `microservices` | Distributed architecture | Service discovery, inter-service communication |
| `monolithic` | Single deployment unit | Shared database, unified codebase |
| `serverless` | Function-as-a-Service | Event triggers, stateless functions |
| `container_orchestration` | Docker + Kubernetes | Containerization, scaling, health checks |
| `ci_cd_pipeline` | Automated deployment | Build, test, deploy automation |

---

## 2 · Pattern Specifications

### 2.1 REST API Pattern
```yaml
pattern_id: rest_api
category: web_development
description: "RESTful web service with standard HTTP semantics"

implied_constraints:
  protocol: http
  methods: [GET, POST, PUT, DELETE, PATCH]
  format: json
  status_codes: standard_http
  cors: enabled
  content_type: "application/json"

common_middleware:
  - request_logging
  - error_handling  
  - input_validation
  - response_formatting

typical_endpoints:
  - path: "/{resource}"
    methods: [GET, POST]
    description: "List and create resources"
  - path: "/{resource}/{id}"
    methods: [GET, PUT, DELETE]
    description: "Read, update, delete specific resource"

technology_recommendations:
  go: [echo, gin, fiber]
  python: [fastapi, django_rest, flask]
  node: [express, nest, koa]
  java: [spring_boot, jersey]

blueprint_layout: api_gateway_pattern
```

### 2.2 JWT Authentication Pattern
```yaml
pattern_id: jwt_authentication
category: security
description: "JSON Web Token-based authentication system"

implied_constraints:
  token_type: jwt
  storage: stateless
  expiry: configurable
  refresh: automatic
  algorithm: [HS256, RS256]

required_endpoints:
  - path: "/auth/login"
    method: POST
    description: "User credential validation"
  - path: "/auth/refresh"
    method: POST  
    description: "Token refresh"
  - path: "/auth/logout"
    method: POST
    description: "Token invalidation"

middleware_components:
  - token_validation
  - user_context_injection
  - route_protection
  - refresh_handling

security_considerations:
  - secure_secret_storage
  - token_expiry_management
  - refresh_token_rotation
  - logout_token_blacklisting

integrates_with: [rest_api, graphql_api, websocket_api]
blueprint_layout: auth_middleware_pattern
```

### 2.3 Microservices Pattern
```yaml
pattern_id: microservices
category: architecture
description: "Distributed system with independent services"

implied_constraints:
  service_communication: http_api
  data_storage: service_per_database
  deployment: independent
  scaling: horizontal
  monitoring: distributed_tracing

required_components:
  - api_gateway
  - service_discovery
  - load_balancer
  - message_queue
  - configuration_management

infrastructure_requirements:
  - container_orchestration
  - service_mesh
  - centralized_logging
  - metrics_collection
  - health_monitoring

communication_patterns:
  synchronous: [http_rest, grpc]
  asynchronous: [message_queue, event_stream]
  
data_patterns:
  - database_per_service
  - event_sourcing