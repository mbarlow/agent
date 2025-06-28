# VISUALIZER.md — Blueprint Generation Engine

> **Role**: Transform Requirements Language into visual blueprints and architectural diagrams
> **Goal**: Generate ASCII and SVG representations that clarify system structure and relationships
> **Method**: Layout algorithms, component mapping, and relationship visualization

---

## 0 · Visualization Principles

1. **Clarity Over Complexity** - Simple, readable diagrams that enhance understanding
2. **Semantic Mapping** - Visual elements directly represent Requirements Language concepts
3. **Hierarchical Layout** - Organize components by architectural layers and dependencies
4. **Multiple Formats** - ASCII for terminals, SVG for web, both optimized for their medium

---

## 1 · Blueprint Generation Algorithms

### 1.1 Component Identification
Map Requirements Language elements to visual components:

```yaml
# Requirements Language Input
intent: web_api_development
domain: user_management
patterns: [rest_api, jwt_authentication, crud_operations]
constraints: {database: postgres, cache: redis}

# Component Mapping
components:
  - type: api_server
    label: "REST API"
    technology: "Echo Framework"
    derived_from: patterns.rest_api
    
  - type: auth_service
    label: "JWT Auth"
    technology: "Middleware"
    derived_from: patterns.jwt_authentication
    
  - type: database
    label: "PostgreSQL"
    technology: "Database"
    derived_from: constraints.database
    
  - type: cache
    label: "Redis Cache"
    technology: "In-Memory Store"
    derived_from: constraints.cache
```

### 1.2 Relationship Mapping
```yaml
# Pattern-Based Relationships
relationships:
  - from: api_server
    to: auth_service
    type: "uses"
    label: "validates tokens"
    
  - from: api_server
    to: database
    type: "reads/writes"
    label: "CRUD operations"
    
  - from: api_server
    to: cache
    type: "caches"
    label: "session data"
    
  - from: auth_service
    to: database
    type: "validates"
    label: "user credentials"
```

### 1.3 Layout Algorithms
```yaml
layout_strategy: hierarchical
layers:
  - name: "Client Layer"
    components: [web_client, mobile_client]
    
  - name: "API Layer"  
    components: [api_server, auth_service]
    
  - name: "Data Layer"
    components: [database, cache, file_storage]

positioning:
  horizontal: center_aligned
  vertical: top_to_bottom
  spacing: {horizontal: 4, vertical: 2}
```

---

## 2 · ASCII Blueprint Format

### 2.1 Component Representation
```
Standard Component Box:
┌─────────────────┐
│   Component     │
│   (Technology)  │
└─────────────────┘

Database Component:
┌─────────────────┐
│  🗄️ PostgreSQL   │
│   (Database)    │
└─────────────────┘

Cache Component:
┌─────────────────┐
│  ⚡ Redis Cache  │
│  (In-Memory)    │
└─────────────────┘

API Component:
┌─────────────────┐
│  🌐 REST API     │
│  (Echo Server)  │
└─────────────────┘
```

### 2.2 Relationship Arrows
```
Connections:
│   vertical connection
─   horizontal connection
┌   top-left corner
┐   top-right corner
└   bottom-left corner
┘   bottom-right corner

Flow Indicators:
───▶  one-way flow
◄──▶  bidirectional
~~~▶  async/event flow
═══▶  data pipeline
```

### 2.3 Complete ASCII Example
```yaml
# Requirements Language
intent: web_api_development
domain: user_management
patterns: [rest_api, jwt_authentication, crud_operations]
constraints: {database: postgres, cache: redis}
```

**Generated ASCII Blueprint:**
```
                    ┌─────────────────┐
                    │  🌐 REST API     │
                    │  (Echo Server)  │
                    └─────────┬───────┘
                              │
                    ┌─────────▼───────┐
                    │  🔐 JWT Auth     │
                    │  (Middleware)   │
                    └─────────┬───────┘
                              │
              ┌───────────────┼───────────────┐
              │               │               │
    ┌─────────▼───────┐ ┌─────▼─────┐ ┌─────▼─────┐
    │  🗄️ PostgreSQL   │ │ ⚡ Redis   │ │ 📁 Users   │
    │   (Database)    │ │  (Cache)  │ │ (Endpoints)│
    └─────────────────┘ └───────────┘ └───────────┘

Data Flow:
  🌐 → 🔐 → 🗄️  (Authentication & Database Access)
  🌐 → ⚡      (Session Caching)
  📁 ← 🗄️      (CRUD Operations)
```

---

## 3 · SVG Blueprint Format

### 3.1 SVG Component Templates
```xml
<!-- API Server Component -->
<g id="api-server" class="component">
  <rect x="10" y="10" width="120" height="60" 
        fill="#e3f2fd" stroke="#1976d2" stroke-width="2" rx="5"/>
  <text x="70" y="30" text-anchor="middle" class="component-label">🌐 REST API</text>
  <text x="70" y="50" text-anchor="middle" class="tech-label">(Echo Server)</text>
</g>

<!-- Database Component -->
<g id="database" class="component">
  <rect x="10" y="100" width="120" height="60" 
        fill="#f3e5f5" stroke="#7b1fa2" stroke-width="2" rx="5"/>
  <text x="70" y="120" text-anchor="middle" class="component-label">🗄️ PostgreSQL</text>
  <text x="70" y="140" text-anchor="middle" class="tech-label">(Database)</text>
</g>

<!-- Cache Component -->
<g id="cache" class="component">
  <rect x="150" y="100" width="120" height="60" 
        fill="#fff3e0" stroke="#f57c00" stroke-width="2" rx="5"/>
  <text x="210" y="120" text-anchor="middle" class="component-label">⚡ Redis</text>
  <text x="210" y="140" text-anchor="middle" class="tech-label">(Cache)</text>
</g>

<!-- Connection Arrow -->
<defs>
  <marker id="arrowhead" markerWidth="10" markerHeight="7" 
          refX="9" refY="3.5" orient="auto">
    <polygon points="0 0, 10 3.5, 0 7" fill="#666"/>
  </marker>
</defs>

<line x1="70" y1="70" x2="70" y2="95" 
      stroke="#666" stroke-width="2" marker-end="url(#arrowhead)"/>
```

### 3.2 SVG Styling
```css
.component-label {
  font-family: Arial, sans-serif;
  font-size: 14px;
  font-weight: bold;
  fill: #333;
}

.tech-label {
  font-family: Arial, sans-serif;
  font-size: 11px;
  fill: #666;
}

.connection {
  stroke: #666;
  stroke-width: 2;
  fill: none;
}

.data-flow {
  stroke: #2196f3;
  stroke-width: 2;
  stroke-dasharray: 5,5;
}
```

---

## 4 · Layout Algorithms

### 4.1 Hierarchical Layout
```yaml
# Layer-based positioning
algorithm: top_down_hierarchy
layers:
  client_layer: {y: 0, components: [web_client, mobile_app]}
  api_layer: {y: 100, components: [rest_api, auth_service]}
  service_layer: {y: 200, components: [business_logic, validation]}
  data_layer: {y: 300, components: [database, cache, storage]}

spacing:
  vertical_layer_gap: 80px
  horizontal_component_gap: 40px
  component_width: 120px
  component_height: 60px
```

### 4.2 Force-Directed Layout
```yaml
# For complex interconnected systems
algorithm: force_directed
forces:
  attraction: {strength: 0.1, distance: 100}
  repulsion: {strength: 0.05, distance: 150}
  gravity: {strength: 0.02, center: [400, 300]}
  
constraints:
  min_distance: 80px
  max_iterations: 1000
  convergence_threshold: 0.01
```

### 4.3 Grid Layout
```yaml
# For uniform component distribution
algorithm: grid_layout
grid:
  columns: 3
  rows: auto
  cell_width: 140px
  cell_height: 80px
  padding: 20px

alignment: center
overflow: wrap_rows
```

---

## 5 · Pattern-Specific Blueprints

### 5.1 REST API Pattern
```yaml
pattern: rest_api
components:
  - API Gateway
  - Route Handlers
  - Middleware Stack
  - Response Formatters

layout: vertical_flow
connections:
  - Request → API Gateway
  - API Gateway → Middleware
  - Middleware → Route Handlers
  - Route Handlers → Response
```

**ASCII Output:**
```
┌─────────────────┐
│   API Gateway   │
│   (Entry Point) │
└─────────┬───────┘
          │
┌─────────▼───────┐
│   Middleware    │
│ (Auth, CORS, etc)│
└─────────┬───────┘
          │
┌─────────▼───────┐
│ Route Handlers  │
│ (Business Logic)│
└─────────┬───────┘
          │
┌─────────▼───────┐
│   Response      │
│ (JSON Format)   │
└─────────────────┘
```

### 5.2 Microservices Pattern
```yaml
pattern: microservices
components:
  - Service A
  - Service B  
  - API Gateway
  - Service Discovery
  - Message Queue

layout: distributed_nodes
connections:
  - Gateway ↔ Services
  - Services ↔ Message Queue
  - Services → Service Discovery
```

**ASCII Output:**
```
                ┌─────────────────┐
                │   API Gateway   │
                │  (Load Balance) │
                └─────────┬───────┘
                          │
          ┌───────────────┼───────────────┐
          │               │               │
┌─────────▼───────┐ ┌─────▼─────┐ ┌─────▼─────┐
│   Service A     │ │ Service B │ │ Service C │
│ (User Mgmt)     │ │ (Orders)  │ │ (Payment) │
└─────────┬───────┘ └─────┬─────┘ └─────┬─────┘
          │               │             │
          └───────────────┼─────────────┘
                          │
                ┌─────────▼───────┐
                │ Message Queue   │
                │   (Events)      │
                └─────────────────┘
```

### 5.3 ETL Pipeline Pattern
```yaml
pattern: etl_pipeline
components:
  - Data Sources
  - Extract Service
  - Transform Engine
  - Load Service
  - Data Warehouse

layout: horizontal_pipeline
connections: sequential_flow
```

**ASCII Output:**
```
┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐
│  Data   │───▶│ Extract │───▶│Transform│───▶│  Load   │───▶│  Data   │
│ Sources │    │ Service │    │ Engine  │    │ Service │    │Warehouse│
└─────────┘    └─────────┘    └─────────┘    └─────────┘    └─────────┘

Data Flow: CSV/API → Parse → Clean/Validate → Format → Store
```

---

## 6 · Interactive Elements

### 6.1 Clickable Components (SVG)
```xml
<g id="api-server" class="component interactive" 
   onclick="showDetails('api-server')">
  <rect x="10" y="10" width="120" height="60" 
        fill="#e3f2fd" stroke="#1976d2" rx="5"/>
  <text x="70" y="35" text-anchor="middle">🌐 REST API</text>
</g>

<script>
function showDetails(componentId) {
  // Show detailed requirements for clicked component
  console.log(`Component: ${componentId}`);
}
</script>
```

### 6.2 Hover Effects
```css
.component:hover {
  filter: drop-shadow(0 4px 8px rgba(0,0,0,0.2));
  cursor: pointer;
}

.component:hover rect {
  stroke-width: 3px;
}
```

### 6.3 Animated Connections
```css
@keyframes data-flow {
  0% { stroke-dashoffset: 20; }
  100% { stroke-dashoffset: 0; }
}

.data-flow {
  stroke-dasharray: 5,5;
  animation: data-flow 2s linear infinite;
}
```

---

## 7 · Blueprint Generation Commands

### 7.1 Basic Blueprint Generation
```
Input: Requirements Language YAML
Process: Component mapping → Layout algorithm → Format generation
Output: ASCII and/or SVG blueprint
```

### 7.2 Pattern-Specific Blueprints
```
Input: Requirements Language + Pattern focus
Process: Apply pattern-specific layout and components
Output: Optimized blueprint for specified pattern
```

### 7.3 Multi-Level Blueprints
```
Input: Complex Requirements Language
Process: Generate overview + detailed views
Output: High-level architecture + component details
```

---

## 8 · Agent Instructions

When generating blueprints:

1. **Analyze Requirements Language** - Extract components and relationships
2. **Select appropriate layout** - Based on patterns and complexity
3. **Generate ASCII version** - For terminal/text environments
4. **Generate SVG version** - For web/document integration
5. **Validate readability** - Ensure diagrams enhance understanding

**Blueprint Response Format:**
```
SYSTEM ARCHITECTURE BLUEPRINT:

ASCII Representation:
[Terminal-friendly diagram]

SVG Representation:
[Web-compatible diagram with styling]

Component Details:
- Component A: [Technology and purpose]
- Component B: [Technology and purpose]
- Connections: [Data flow and relationships]

Blueprint Metrics:
- Components: X
- Connections: Y  
- Complexity: [Low/Medium/High]
- Layout: [Algorithm used]
```

---

## 9 · Example Blueprints

### 9.1 Simple Web API
**Requirements Language:**
```yaml
intent: web_api_development
domain: user_management
patterns: [rest_api, jwt_authentication]
constraints: {database: postgres}
```

**Generated Blueprint:**
```
                Client Applications
                        │
                ┌───────▼───────┐
                │  🌐 REST API   │
                │ (Echo Server) │
                └───────┬───────┘
                        │
                ┌───────▼───────┐
                │  🔐 JWT Auth   │
                │ (Middleware)  │
                └───────┬───────┘
                        │
                ┌───────▼───────┐
                │ 🗄️ PostgreSQL  │
                │  (Database)   │
                └───────────────┘

Endpoints: /auth/login, /auth/register, /users/*
Security: JWT tokens with middleware validation
Data: User profiles and authentication records
```

### 9.2 Complex Microservices
**Requirements Language:**
```yaml
intent: system_design
domain: e_commerce
patterns: [microservices, event_driven, api_gateway]
constraints: {scale: high, deployment: kubernetes}
```

**Generated Blueprint:**
```
              ┌─────────────────┐
              │   API Gateway   │
              │ (Load Balancer) │
              └─────────┬───────┘
                        │
        ┌───────────────┼───────────────┐
        │               │               │
┌───────▼───┐   ┌───────▼───┐   ┌───────▼───┐
│User Service│   │Order Svc  │   │Payment Svc│
│   (Auth)   │   │ (Cart)    │   │(Billing)  │
└───────┬───┘   └───────┬───┘   └───────┬───┘
        │               │               │
        └───────────────┼───────────────┘
                        │
                ┌───────▼───────┐
                │ Event Stream  │
                │   (Kafka)     │
                └───────────────┘

Scaling: Kubernetes pods with horizontal autoscaling
Events: User.Created, Order.Placed, Payment.Processed
Storage: Each service has dedicated database
```

---

**Version**: v1.0 — 2025-01-28