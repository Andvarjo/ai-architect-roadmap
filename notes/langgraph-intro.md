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

- [InMemorySaver and `thread_id` config](#memory_setup) enable state persistence across invocations
- Pass the [checkpointer to compile()](#graph_with_memory) to enable memory

Execution:

- Each [invoke with the same `thread_id`](#l4_execution) accesses the same persisted state
- State accumulates across multiple invocations within the same thread
- Different `thread_id`s maintain separate conversation histories

## Takeaways 5

Setup:

- [Node_a uses `interrupt()`](#interrupt_node) to pause execution when unexpected input occurs
- [Checkpointer enables interrupts](#l5_memory) by saving state between pause and resume

Execution:

- When interrupt is called, the [graph pauses](#l5_execution) and waits for human input
- The admin response determines whether to continue execution or end
- Graph state is preserved during the pause and restored when resuming
