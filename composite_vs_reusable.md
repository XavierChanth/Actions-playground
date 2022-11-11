# Composite Vs. Reusable Workflows

A composite actions allows you to call it from within a list of steps, and any
steps taken within the composite action will act as a single step. This is
useful when:
  - You have already checked out the repository containing the composite action that you want to use
  - The action doesn't require any secrets
  - You don't plan to use different types of shells for the action (i.e. matrix runs with different os)

A reusable workflow (i.e. using the 'workflow_call' trigger) allows you to call a job without a steps list,
instead just calling the single job with a 'uses' clause where the steps list normally would be.
This is useful when:
  - You only need to run the steps defined in the workflow you are calling
  - You can accomplish any additional steps using a 'needs' clause
  - You have access to the secrets needed (if any), especially if they use the same name
  - Inputs are the only thing that need to change across multiple runs.