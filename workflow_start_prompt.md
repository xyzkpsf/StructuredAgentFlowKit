<PromptRequest>

  <Goal>
  Implement the plan detailed in </Implementation_plan> using the two-file system. Execute tasks sequentially and **continuously** based on the state in </Implementation_state>, updating the state after each successful task. **Only stop if an error occurs or the plan is complete.** Use </Implementation_plan> as read-only Long-Term Memory (LTM) and </Implementation_state> as read/write Short-Term Memory (STM).
  </Goal>

  <Context>
    <Implementation_plan>
      </Implementation_plan>

    <Implementation_state>
      </Implementation_state>

  </Context>

  <Request>
    Please perform the following workflow **continuously until completion or error**:

    <Workflow_Instructions>
    **Execution Cycle:**
    1.  **Read STM:** Consult </Implementation_state> to identify the specific task in `## Current Task / Next Action`. If this section is empty or indicates completion, stop and report the plan is finished.
    2.  **Read LTM:** Consult </Implementation_plan> to understand the details and requirements for executing the identified task.
    3.  **Execute Task:** Perform the necessary actions (e.g., create/modify files, run commands) precisely as required by the task description in the LTM.
    4.  **Handle Errors:**
        * If an error occurs during execution, **STOP** the current task and the entire workflow immediately.
        * Record the specific error message and context in the `## Errors / Blockers` section of </Implementation_state>.
        * Update `## Last Action Summary` indicating failure and the reason.
        * Do **NOT** update `## Completed Items`. Ensure `## Current Task / Next Action` still reflects the task that failed.
        * Report the error and the halt state to the user. **WAIT** for further instructions. Do **NOT** attempt any further tasks.
    5.  **Update STM (on Success):**
        * If the task completes successfully, meticulously update </Implementation_state> following the `Interaction Protocol` defined below (Update State, Log Completion, Summarize Action, Clear Errors, Set Next Task).
    6.  **Report and Proceed (on Success):**
        * After successfully updating the STM, briefly inform the user that the task (`[Completed Task ID/Name]`) is complete and the state file </Implementation_state> is updated.
        * State the *new* task now listed under `## Current Task / Next Action` in the updated STM (`[New Task ID/Name]`).
        * **Immediately proceed** to the next execution cycle (starting from Step 1) with this new task. **Do NOT wait for user confirmation.**
    </Workflow_Instructions>

    <Important_Files>
      </Implementation_plan>:
        **Role:** Long-Term Memory (Plan). Contains the detailed, step-by-step plan for implementation.
        **Constraint:** This file is **READ-ONLY**. Do NOT modify it during the implementation process. Refer to it to understand the requirements for each task identified in the STM.

      </Implementation_state>:
        **Role:** Short-Term Memory (State Tracker). Contains the dynamic state of the implementation process.
        **Interaction Protocol:**
        1.  **ALWAYS READ** this file **BEFORE** starting any action to determine the `Current Task / Next Action`.
        2.  **ALWAYS UPDATE** this file **AFTER** completing an action successfully and **BEFORE** reporting/proceeding (Step 6). Accurate updates are CRITICAL. Updates MUST include:
            * Updating `## Overall State` (e.g., phase, progress summary).
            * Moving the completed task ID/Description from `## Current Task / Next Action` to `## Completed Items` (append it).
            * Detailing the action performed, outcome, and observations in `## Last Action Summary`.
            * Clearing previous errors in `## Errors / Blockers` since the action was successful.
            * Identifying the **NEXT** sequential task from </Implementation_plan> (based on the updated `## Completed Items`) and populating `## Current Task / Next Action` with its ID/Description and setting its Status to 'Pending'. If no more tasks remain in the plan, indicate completion here or leave it empty.
    </Important_Files>

<Initial_Action>
Carefully read the current state from </Implementation_state>. Identify the first task listed under `## Current Task / Next Action`. Verify you understand the task by briefly stating it. **Ask the user ONLY ONCE to confirm you should begin implementing this first task.** Once confirmed, start the continuous Execution Cycle described above.
</Initial_Action>

</PromptRequest>
