# ⚡ GoHyperrr

> The AI-Observable, Event-Native Modular Commerce Engine. Built for autonomous agents and modern developers.

---

Welcome to the home of **Hyperrr**, a next-generation distributed commerce engine designed from the ground up to be **AI-observable, event-driven, and strictly modular**. 

Unlike legacy commerce systems, Hyperrr treats all business operations as deterministic, replayable DAG (Directed Acyclic Graph) workflows connected by a unified event fabric. It exposes dynamic capabilities to both human developers via **GraphQL** and autonomous AI agents via the **Model Context Protocol (MCP)**.

---

## 🏗️ System Architecture

```text
               ┌─────────────────────────────────┐
               │    AI Agents & Web Clients      │
               └────────────────┬────────────────┘
                                │ (GraphQL / MCP)
                                ▼
               ┌─────────────────────────────────┐
               │         hyperrr Core            │
               │  (Workflow Engine + Event Bus)  │
               └────────┬────────┬────────┬──────┘
                        │        │        │
           ┌────────────┘        │        └────────────┐
           ▼                     ▼                     ▼
 ┌───────────────────┐ ┌───────────────────┐ ┌───────────────────┐
 │   commerce mod    │ │     auth mod      │ │   custom mod      │
 │  (Order/Cart/...) │ │ (APIKey/JWT/...)  │ │  (Your code)     │
 └─────────┬─────────┘ └─────────┬─────────┘ └─────────┬─────────┘
           │                     │                     │
           └─────────────────────┼─────────────────────┘
                                 │ (Decoupled Imports)
                                 ▼
                       ┌───────────────────┐
                       │        mdk        │
                       │ (Development Kit) │
                       └───────────────────┘
```

---

## 📦 Core Repositories

| Repository | Purpose | Language / Tech |
| :--- | :--- | :--- |
| [**`hyperrr`**](https://github.com/GoHyperrr/hyperrr) | The core orchestration kernel containing the workflow engine, memory lock manager, event bus, and MCP gateway. | Go, Cobra, Viper, gqlgen |
| [**`mdk`**](https://github.com/GoHyperrr/mdk) | The Module Development Kit. A decoupled interface layer providing unit testing runtimes and mocks so modules can compile independently. | Go, GORM |
| [**`commerce`**](https://github.com/GoHyperrr/commerce) | High-performance sub-modules for catalog management, shopping carts, orders, fulfillment, search, and support. | Go, GORM |
| [**`auth`**](https://github.com/GoHyperrr/auth) | Pluggable authorization providers including standard email/password, JWT verification, and secure API Key generation. | Go, bcrypt |

---

## 🚀 Key Features

* **🤖 AI Agent Native**: Integrated support for Model Context Protocol (MCP) allowing tools, workflows, and dashboard UIs to be rendered dynamically inside AI agent interfaces.
* **⚡ Event-Driven DAGs**: Complex operations (like order fulfillment sagas) are modeled as declarative workflows with built-in rollback compensations.
* **🧩 Strict Compiler Decoupling**: Functional modules compile and run independently of the core engine, utilizing `go.work` workspaces locally and standard Go module pseudo-versions in isolated CI pipelines.
* **📊 Visual Observability**: Projector-based lineage tracking lets you trace every step of a workflow run in real-time.

---

## 🛠️ Getting Started (Local Development)

Hyperrr uses Go Workspace (`go.work`) to link modules together locally for seamless editing.

1. **Clone the entire stack**:
   ```bash
   git clone https://github.com/GoHyperrr/hyperrr.git
   git clone https://github.com/GoHyperrr/mdk.git
   git clone https://github.com/GoHyperrr/commerce.git
   git clone https://github.com/GoHyperrr/auth.git
   ```

2. **Setup the Go Workspace**:
   Create a `go.work` file in your parent directory containing:
   ```go
   go 1.25.5

   use (
       ./auth
       ./commerce
       ./hyperrr
   )

   replace github.com/GoHyperrr/mdk => ./mdk
   ```

3. **Run the server**:
   ```bash
   cd hyperrr
   go run ./cmd/hyperrr server
   ```

---

## 🤝 Contributing

We welcome contributions of all kinds! Whether you are writing new commerce adapters, enhancing the workflow orchestration engine, or building new AI tools, check out the [Developer Guide](https://github.com/GoHyperrr/hyperrr/blob/main/developer.md) to get started.

Let's build the future of agentic commerce together. ⚡
