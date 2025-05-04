<PromptRequest>

  <Goal>
    Generate a detailed **implementation plan** in Markdown format for the task described in <TaskDescription/>. The plan should be based on an analysis of the current context and suitable for review before actual implementation begins.
  </Goal>

  <Context>
    <TaskDescription>
      </TaskDescription>

    <RelevantCodebase>
      </RelevantCodebase>

    <RelevantDocumentation>
      </RelevantDocumentation>

    <CurrentState>
      </CurrentState>

    <RelevantTechnologies>
      </RelevantTechnologies>

  </Context>

  <Request>
    Please perform the following steps:

    <AnalysisPhase>
      1.  **Analyze Current Context:**
          * Conduct a comprehensive analysis of the <TaskDescription/> in relation to the <RelevantCodebase/>, <RelevantDocumentation/>, and <CurrentState/>.
          * Evaluate potential impacts, dependencies, and prerequisites for the task.
          * Identify potential challenges, risks, unknowns, or areas needing further investigation based on the provided context.
          * **Summarize these findings clearly.**
    </AnalysisPhase>

    <PlanningPhase>
      2.  **Outline a Detailed Implementation Plan:**
          Based on the analysis, **outline** a clear, actionable plan describing *how* the task will be implemented. This plan should detail the approach, broken down into **phases** with specific **tasks** and **steps** where applicable, covering the following aspects (adapt relevance based on the task):

          * **<DesignAndArchitecturePlan title="Planned Design & Architecture">**
              * **Outline necessary design decisions** or architectural changes needed to implement the <TaskDescription/>.
              * **Describe key components** to be created or modified and their interactions.
              * Identify any necessary interface changes (APIs, function signatures, UI components).
              * *(Plan the 'what' and 'how' of the structure; do not write detailed specs unless requested by the task).*
          * **</DesignAndArchitecturePlan>**

          * **<ImplementationDetailsPlan title="Planned Implementation Steps">**
              * **Break down the core implementation work** into logical tasks or steps.
              * Identify specific modules, functions, or classes to be developed or modified.
              * Outline algorithms or logic flows for critical parts of the task.
              * Specify configuration changes, environment variable needs, etc.
              * *(Plan the sequence of development activities; do not write the code).*
          * **</ImplementationDetailsPlan>**

          * **<DataManagementPlan title="Planned Data Management (If Applicable)">**
              * **Outline any required database schema changes**, migrations, or data transformations.
              * Describe strategies for handling existing data or seeding new data if needed.
              * *(Plan data-related tasks; do not write migration scripts).*
          * **</DataManagementPlan>**

          * **<TestingStrategyPlan title="Planned Testing Strategy">**
              * **Outline the approach for testing** the implemented task (Unit, Integration, E2E, Manual).
              * **Identify key scenarios** to test based on <TaskDescription/> and <RelevantDocumentation/> (happy paths, edge cases, error conditions).
              * Describe requirements for test data or mocking.
              * Specify any new test cases needed or existing ones to update.
              * *(Plan how quality will be assured; do not write the tests).*
          * **</TestingStrategyPlan>**

          * **<DeploymentPlan title="Planned Deployment/Rollout (If Applicable)">**
              * **Outline the steps** for deploying the changes (e.g., CI/CD pipeline updates, manual steps).
              * Identify dependencies for deployment (e.g., infrastructure changes, other team releases).
              * Describe any phased rollout strategy if applicable.
              * *(Plan the release process; do not perform the deployment).*
          * **</DeploymentPlan>**

          * **<RollbackPlan title="Planned Rollback Strategy (If Applicable)">**
              * **Outline the strategy** for reverting the changes if issues arise post-deployment.
              * Identify steps needed to restore the previous state.
              * *(Plan for failure recovery).*
          * **</RollbackPlan>**
    </PlanningPhase>

  </Request>

  <Deliverable>
    The expected output is a **detailed implementation plan** in **Markdown format**. This document must contain:
    1.  A clear summary of the **Analysis Findings** (impacts, dependencies, risks, challenges).
    2.  A detailed **Implementation Plan Outline** covering the relevant planned aspects (Design/Architecture, Implementation Steps, Data Management, Testing, Deployment, Rollback) as described in the request.
    3.  The plan must be structured with clear **Phases** and associated **Tasks/Steps** for each phase, making it suitable for review and tracking before implementation begins.
  </Deliverable>

</PromptRequest>
