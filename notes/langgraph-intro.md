# LangGraph Essentials (Python) — course notes

**Course:** [LangGraph Essentials — Python](https://academy.langchain.com/courses/take/langgraph-essentials-python/lessons/69419153-introduction) (LangChain Academy)
**Date:** 2026-04-28 (Week 1, Day 2)
**Reference repo (kept local, not in this repo):** `langchain-ai/lca-langgraph-essentials`

## Lessons covered

| # | Lesson | Concept |
|---|---|---|
| L1 | Nodes | State as TypedDict / dataclass / Pydantic; nodes as pure functions |
| L2 | Edges | Reducers + parallel execution via `Annotated[..., operator.add]` |
| L3-L4 | Conditional edges + memory | `InMemorySaver`, `thread_id`, persisted state across invocations |
| L5 | Interrupt | Native `interrupt()` for human-in-the-loop, paired with checkpointer |
| L6 | Email Agent (project) | Intent classification + conditional routing + HITL approval |

---

## Takeaways 1

- State: All nodes share the same [state](#state_definition) which can be a Python TypedDict, dataclass, or a Pydantic BaseModel
- Nodes: Defined as simple [Python functions](#node_function) that receive state as input and return updated state

Execution (invoke):

- Runtime: When you call [invoke](#graph_invoke), the graph initializes the input state from your invoke statement and determines which nodes to run
- State Flow: Each node receives the current state as input, executes its logic, and returns an updated state
- Graph Return: After all nodes complete execution, the graph returns the final state value

## Takeaways 2

Setup:

- State: You added a [reducer function](#state_with_reducer) in the state definition using Annotated with operator.add
- Graph: You used [add_edge()](#parallel_graph) to create parallel paths from node 'a' to both 'b' and 'c'

Execution:

- Runtime: [Nodes b and c](#parallel_nodes) operate in parallel, executing simultaneously
- The reducer function merges the values returned from parallel branches
- Results from node b and c are stored to state before starting node bb and cc

Result:

- The [final result](#parallel_execution) contains all values added to `nlist` by all nodes
- Values accumulate in the order nodes complete execution

## Takeaways 3 and 4

Setup:

- [