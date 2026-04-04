Requirements:
- Provide capability to execute several coding sessions in parallel. Each session should be able to take assignment in the form of documented task, disambiguate, execute, test, and commit changes. 
- Code commits made during session parallel concurrent sessions must not conflict with each other. Use git worktrees to isolate commits from each other.
- Central agent (Orchestrator) should be able to coordinate the work of the sessions
- Central agent should be able to monitor the progress of the sessions and provide feedback to the user.
- Central agent should be able to stop the sessions if session agent is stuck or is not making progress.


Implementation plan:
- [ ] Study Claude teams of agents and how they are used to coordinate the work of the agents.
- [ ] Design agentic SDLC workflow. Define roles, skills, agents, hooks and subagents
- [ ] Refine agentic SDLC workflow for numio needs. Some steps could be:
    - [ ] Task validation. Create special sub-agent to validate the task. Task must meet quality criteria: state clearly scope, avoid ambiguity, provide acceptance criteria, provide quality gates.
    - [ ] Requirements analysis from task. 
    - [ ] Disambiguation of requirements. Session may pause to ask the user for clarification. Agent should use Claude Channels to message the user for clarifications.
    - [ ] Execution of the task. Session should be able to execute the task in parallel with other sessions.
    - [ ] Testing of the task. Create special testing sub-agent to test the task. 
    - [ ] Commit of the changes. Session should be able to commit the changes in parallel with other sessions.
    - [ ] Cleanup of the session. Session should be able to cleanup the session after the task is completed.
- [ ] Design of orchestrator. Decide if we can use Claude teams of agents, or should be we implement a dedicated orchestrator script. 
- [ ] Decide if current agentpack can be used to orchestrate the sessions. If not, we need to implement a dedicated orchestrator script.
- [ ] Design orchestrator workflow:
    - [ ] Orchestrator should be able to start the sessions.
    - [ ] Orchestrator should be able to monitor the progress of the sessions.
    - [ ] Orchestrator should be able to stop the sessions if session agent is stuck or is not making progress.
    - [ ] Orchestrator should be able to provide feedback to the user on the progress of the sessions.
