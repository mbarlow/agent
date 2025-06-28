# COMPILER.md — Requirements Language Processor

> **Role**: Transform natural language prompts into optimized Requirements Language (RL)
> **Goal**: 40%+ token reduction while improving clarity and implementation confidence
> **Output**: Structured YAML specification + optimized prompt package

---

## 0 · Compilation Principles

1. **Semantic Preservation** - Never lose user intent during optimization
2. **Pattern Recognition** - Map user requests to established solution templates  
3. **Constraint Extraction** - Identify technical and business requirements
4. **Ambiguity Resolution** - Convert unclear requests into specific implementations

---

## 1 · Requirements Language Specification

### 1.1 Core Structure
```yaml
intent: <primary_goal_classification>
domain: <technical_problem_space>
patterns: [<solution_templates>]
constraints:
  <technical_requirements>
style:
  <implementation_preferences>
output:
  <expected_deliverables>
context_map:
  - <semantic_relationships>
```

### 1.2 Intent Classifications
| Intent | Description | Examples |
|--------|-------------|----------|
| `code_generation` | Creating new applications | "Build a REST API", "Create a web app" |
| `system_design` | Architecture and planning | "Design a microservice", "Plan a database" |
| `optimization` | Performance improvements | "Make this faster", "Reduce memory usage" |
| `integration` | Connecting systems | "Add authentication", "Connect to database" |
| `analysis` | Understanding and evaluation | "Analyze this code", "Review performance" |
| `documentation` | Writing docs and guides | "Document this API", "Create user guide" |

### 1.3 Domain Classifications
| Domain | Focus Area | Common Patterns |
|--------|------------|-----------------|
| `web_development` | Frontend/backend apps | `rest_api`, `spa_framework`, `responsive_design` |
| `data_processing` | ETL, analytics, ML | `etl_pipeline`, `data_validation`, `ml_inference` |
| `infrastructure` | DevOps, deployment | `containerization`, `ci_cd`, `monitoring` |
| `mobile_development` | iOS/Android apps | `native_app`, `cross_platform`, `offline_sync` |
| `system_integration` | API connections | `webhook_handling`, `third_party_auth`, `data_sync` |

---

## 2 · Compilation Process

### 2.1 Analysis Phase
```yaml
# Input: "I want to build a web API for user management with authentication"

# Extract core intent
intent: code_generation  # Building new application

# Identify domain  
domain: web_development  # Web-based application

# Recognize patterns
patterns: [rest_api, user_management, jwt_authentication]

# Extract constraints
constraints:
  architecture: rest       # RESTful design implied
  security: authentication # Auth explicitly mentioned
  data_model: users       # User management implies user data
```

### 2.2 Optimization Phase
```yaml
# Original prompt analysis
original_tokens: 84
ambiguities: ["which framework?", "what database?", "deployment target?"]

# Pattern-based defaults
constraints:
  language: go            # Default for REST APIs
  framework: echo         # Go web framework
  database: postgres      # Relational for user data
  authentication: jwt     # Industry standard

# Optimized specifications
optimized_tokens: 47      # 44% reduction
clarity_score: 9.2        # High implementation confidence
```

### 2.3 Output Generation
```yaml
# Final Requirements Language
intent: web_api_development
domain: user_management
patterns: [rest_api, jwt_authentication, crud_operations]
constraints:
  language: go
  framework: echo
  database: postgres
  security: jwt_tokens
  validation: strict
style:
  architecture: clean
  error_handling: comprehensive
  testing: unit_integration
output:
  api_endpoints: true
  authentication: middleware
  documentation: openapi
  tests: comprehensive
context_map:
  - "user_management" -> operations: ["create", "read", "update", "delete"]
  - "jwt_authentication" -> middleware: ["token_validation", "refresh_handling"]
  - "postgres" -> features: ["connection_pooling", "migrations", "transactions"]
```

---

## 3 · Pattern Library Integration

### 3.1 Pattern Matching Algorithm
1. **Keyword Analysis** - Extract technical terms and domain vocabulary
2. **Intent Mapping** - Match user goals to solution categories
3. **Constraint Inference** - Derive technical requirements from context
4. **Template Application** - Apply best-practice patterns for the domain

### 3.2 Pattern Composition
```yaml
# Multiple patterns can be composed
patterns: [rest_api, jwt_authentication, rate_limiting, swagger_docs]

# Patterns inherit constraints
rest_api:
  implies: [http_methods, json_responses, status_codes]
jwt_authentication:  
  implies: [token_middleware, refresh_endpoints, user_sessions]
```

### 3.3 Constraint Validation
```yaml
# Detect conflicts
patterns: [rest_api, graphql_api]  # CONFLICT: Choose one API style
resolution: "REST API selected based on user familiarity context"

# Validate compatibility  
language: go
framework: django  # CONFLICT: Django is Python framework
resolution: "Echo framework selected for Go language constraint"
```

---

## 4 · Quality Metrics

### 4.1 Efficiency Measurements
```yaml
metrics:
  token_reduction: "44%"        # (84 → 47 tokens)
  clarity_improvement: "9.2/10" # Implementation confidence  
  ambiguity_resolution: "3/3"   # Questions answered
  pattern_confidence: "95%"     # Template match accuracy
```

### 4.2 Validation Criteria
- **Semantic Preservation**: Original intent maintained
- **Implementation Readiness**: Clear enough for development
- **Technology Coherence**: Compatible tech stack choices
- **Best Practice Alignment**: Industry-standard patterns applied

---

## 5 · Compilation Commands

### 5.1 Basic Compilation
```
Input: [natural language prompt]
Process: Apply §2 compilation process
Output: Requirements Language + metrics + optimized prompt
```

### 5.2 Pattern-Specific Compilation  
```
Input: [prompt] + preferred patterns
Process: Apply specified patterns with validation
Output: Requirements Language optimized for given patterns
```

### 5.3 Constraint-Driven Compilation
```
Input: [prompt] + technical constraints
Process: Compile within specified technology boundaries
Output: Requirements Language respecting all constraints
```

---

## 6 · Example Compilations

### 6.1 Simple Web API
**Input**: "Create an API for managing blog posts"

**Compiled RL**:
```yaml
intent: code_generation
domain: web_development  
patterns: [rest_api, crud_operations, content_management]
constraints:
  resource: blog_posts
  operations: [create, read, update, delete, list]
  data_validation: required
style:
  api_design: restful
  response_format: json
output:
  endpoints: crud_complete
  validation: input_schemas
  documentation: api_spec
```

**Metrics**: 67% token reduction, 8.8/10 clarity

### 6.2 Complex Data Pipeline
**Input**: "Build a system that processes CSV files, cleans data, runs ML models, and shows results on a dashboard"

**Compiled RL**:
```yaml
intent: system_design
domain: data_processing
patterns: [etl_pipeline, ml_inference, data_visualization, batch_processing]
constraints:
  input_format: csv
  processing: data_cleaning
  ml_component: model_inference  
  output: dashboard
  scale: production_ready
style:
  architecture: pipeline
  processing: distributed
  monitoring: comprehensive
output:
  data_ingestion: automated
  ml_pipeline: trained_models
  dashboard: interactive
  monitoring: real_time
context_map:
  - "etl_pipeline" -> stages: ["extract_csv", "transform_clean", "load_processed"]
  - "ml_inference" -> components: ["model_loading", "batch_prediction", "result_storage"]
  - "dashboard" -> features: ["real_time_updates", "interactive_charts", "drill_down"]
```

**Metrics**: 52% token reduction, 9.0/10 clarity

---

## 7 · Agent Instructions

When processing user prompts:

1. **Load this COMPILER.md** to understand Requirements Language structure
2. **Analyze user input** using §2.1 process
3. **Apply pattern matching** from §3 algorithms
4. **Generate Requirements Language** following §1 specification
5. **Calculate metrics** using §4 measurements
6. **Output structured result** with RL + metrics + optimized prompt

**Response Format**:
```
COMPILED REQUIREMENTS LANGUAGE:
[YAML output]

OPTIMIZATION ANALYSIS:
- Original: X tokens
- Optimized: Y tokens (Z% reduction)  
- Clarity score: N/10
- Pattern confidence: M%

OPTIMIZED PROMPT PACKAGE:
[Final prompt ready for implementation]
```

---

**Version**: v1.0 — 2025-01-28