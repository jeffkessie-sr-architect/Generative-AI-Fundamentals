# Compound AI Systems


# 1. What Is a Compound AI System?

A Compound AI System is an application that combines multiple components to deliver an intelligent result.

It is more than a single AI model making one request. It coordinates a model with other systems, such as:

**Retrieval**: Finds relevant information from documents or databases.

**Tools**: Allows the AI to perform tasks, such as searching or calling external services.

**Classical ML**: Provides predictions, classifications, or recommendations.

**Memory**: Stores relevant information from previous interactions.

**Guardrails**: Helps ensure responses follow safety and business rules.

**Governed data**: Provides trusted, managed, and controlled information for the application.


# 2. How Do Compound AI System Work?

The different components work together to answer a user's request.


              ┌──────────────────────────┐
              │        USER INPUT        │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │         AI MODEL         │
              │    Understands Request   │
              └────────────┬─────────────┘
                           │
                 ┌─────────┴─────────┐
                 │                   │
                 ▼                   ▼
       ┌──────────────────┐  ┌──────────────────┐
       │    RETRIEVAL     │  │      TOOLS       │
       │ Find relevant    │  │ Perform tasks    │
       │ information      │  │ and actions      │
       └────────┬─────────┘  └────────┬─────────┘
                │                     │
                └──────────┬──────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │       CLASSICAL ML       │
              │ Predictions and          │
              │ classifications          │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │          MEMORY          │
              │ Stores relevant context  │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │        GUARDRAILS        │
              │ Checks safety and        │
              │ business rules           │
              └────────────┬─────────────┘
                           │
                           ▼
              ┌──────────────────────────┐
              │     FINAL RESPONSE       │
              │       To the User        │
              └──────────────────────────┘


**Note: This is a conceptual diagram. In a real application, components may run in different orders or be called only when needed.**

# 3. Compound AI System?

A single model call may not be enough for complex applications.

Combining multiple components provides several benefits:

**Better answers**: Retrieval provides relevant information.
More capabilities: Tools allow the AI to perform actions.
Better predictions: Classical ML handles specialized prediction tasks.

**Context awareness**: Memory helps retain relevant information.
Safer responses: Guardrails enforce application rules.
Trusted information: Governed data helps maintain data quality and control.


# 4. Simple Real-World Example

Consider a company customer-support assistant.

When a customer asks about an order:

The AI model understands the question. (**Mosaic AI Model Serving / Foundation Model APIs**)

Retrieval finds relevant company policies. (**Mosaic AI Vector Search**)

A tool retrieves the customer's order details. (**MCP Servers / Databricks SQL**)

Memory provides relevant conversation context. (**Agent Memory and Sessions (Lakebase)**)

Guardrails check that the response follows company policies. (**Unity Gateway**)

The assistant generates the final answer.


         Customer Support Workflow

       Customer asks about order
                  |
                  v
          AI understands request
                  |
                  v
          Retrieve company policy
                  |
                  v
          Tool checks order status
                  |
                  v
          Retrieve relevant memory
                  |
                  v
          Apply safety guardrails
                  |
                  v
          Generate final response
                  |
                  v
          Answer customer

# 5. Conclusion

A Compound AI System is not just one AI model. It is an application that coordinates multiple components, including retrieval, tools, classical ML, memory, and guardrails.

An application that coordinates a model with retrieval, tools, classical ML, memory, and guardrails, all grounded in governed data.