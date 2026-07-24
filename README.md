# introduction-to-deep-agents

## What is an agent?
- A model calling tools in a loop until it completes a task and returns a result.
![What is an agent](assets/what_is_an_agent.png)

## What is a harness?
- The harness is everything that connects the model to the real world, everything around the model that helps it complete tasks. This is made up of skills, memory, the base system prompt, tools, subagents, and any additional context.
![What is a harness](assets/what_is_a_harness.png)

## what is the job of a harness?
- To get the model the right context at the right time for the given task. A model is only as powerful as the context that it's given, and so the harness exists to bridge this gap.

## Why do we need a harness?
- Agents need:
    - Take actions in an environment: Take actions via tools, read and write files, execute code
    - Connect to your data: Load memories, skills, and domain knowledge at the right moment
    - Manage growing context: Summarize history and offload large results across long runs
    - Parallelize tasks: Delegate to general or specialized subagents running in isolated context windows
    - Stay in the loop: Pause for human approval at critical decision points
    - Improve over time: Update memory, skills, and prompts based on real usage

## What is Deep Agents?
- Deep Agents is the easiest way to start building agents and applications that are powered by LLMs—with built-in capabilities for task planning, file systems for context management, subagent-spawning, and long-term memory. You can use deep agents for any task, including complex, multi-step tasks. There are four main capabilities of the Deep Agents harness.
    1. Execution Environment: Backbon of a Harness. Has four layers.
        - Tools: custom functions, APIs, and databases the agent can call
        - Virtual filesystem: file tools backed by pluggable backends
        - Filesystem permissions: declarative access control over which paths agents can read or write
        - Code execution: sandboxed shell execution and an in-process JavaScript interpreter
    2. Context Management:
        - Skills: on-demand domain knowledge loaded progressively from skill files
        - Memory: persistent instructions and preferences loaded at startup from AGENTS.md files
        - Summarization and context offloading: automatic compression of conversation history and large tool results.
            - Input context: System prompt, memory, skills, and tool prompts define what the agent starts with.
            - Compression: Built-in offloading and summarization compress conversation history and large intermediate results.
            - Isolation: Subagents quarantine heavy subtasks and return only final results (see Delegation).
            - Long-term memory: Persistent storage in the virtual filesystem carries information across threads.
        - Prompt caching: static prompt sections are cache-eligible to speed up inference and reduce cost on supported models
    3. Delegation: As agents run for longer amounts of time and take on complex workflows, they need to plan and organize tasks and then use subagents to delegate work.
        - Task planning: a built-in write_todos tool for structured task tracking
        - Subagents: The harness includes a built-in task tool that lets the main agent create ephemeral subagents for isolated, long-running, multi-step, or parallel tasks. Subagents execution provides.
            - Fresh context: Each invocation creates a new agent instance with its own context.
            - Autonomous execution: The subagent runs independently until completion.
            - Single handoff: It returns one final report to the main agent.
            - Configurable strategy: Use the default general-purpose subagent (enabled by default) or define custom subagents.
            - Stateless messaging: Subagents are stateless and cannot send multiple messages back.
            - Context and token efficiency: Heavy subtask work stays isolated and is compressed into a compact result.

    4. Steering: The steering component gives humans control over agent behavior at runtime and sets filesystem permissions for agent work.
        - Human-in-the-loop approval: 
            - This gives you a runtime safety and control layer for destructive operations, expensive API calls, and interactive debugging.
        - Interrupts

    ![Deepagent categories](assets/agent_harness_capabilities.svg)

- Middleware
    ![Deepagent Middleware One](assets/deepagent_middleware_1.png)
    ![Deepagent Middleware Two](assets/deepagent_middleware_1.png)

