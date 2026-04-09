---
title: Configure Runtime Argument Schemas
description: Define structured runtime argument input forms for automations using component.yaml runtimeArguments in schema version 1.2.
---

## Prerequisite

1. Create or import an automation. See [Schedule Your First Automation](schedule-your-first-automation.md).

=== "WSO2 Integrator: BI"
    ## WSO2 Integrator: BI

    Devant derives the runtime argument schema from configured Ballerina entry/startup parameters and auto-generates `component-model.json`.

    ### Step 1: Open the automation in Cloud Editor
    1. Open the automation **Overview** page.
    2. Click **Open in Cloud Editor**.

    ### Step 2: Add Startup Parameters
    1. In WSO2 Integrator: BI, go to **Automation** and click **Configure**.
    2. Expand **Advanced Configurations** and click **Add Parameter**.
    3. Select a type, provide a name, and click **Add**.

    ### Step 3: Push changes and build
    1. Click **Create** or **Save**.
    2. Push changes and wait until build status is **Completed**.

        <div style="width: 100%;">
        ![Configure startup parameters in BI](../../assets/img/get-started/configure-runtime-argument-schema/runtime-args-bi.gif)
        </div>

    ### Step 4: Verify the generated runtime argument form

    1. In Devant, go to the automation **Overview** page, click **Test with Arguments**.

        <div style="width: 100%;">
        ![Open generated runtime argument form](../../assets/img/get-started/configure-runtime-argument-schema/runtime-args-bi-trigger.gif)
        </div>

    ### Supported argument types

    - `string`
    - `int`
    - `float`
    - `decimal`
    - `byte`

=== "component.yaml (v1.2)"
    ## component.yaml (v1.2)
    Define runtimeArguments in .choreo/component.yaml to render a structured, validated runtime argument form in Devant.

    ### Step 1: Create or update `.choreo/component.yaml`

    1. In your project root, create `.choreo/component.yaml` if it does not exist.
    2. Set `schemaVersion: 1.2`.

    ### Step 2: Add `runtimeArguments`

    1. Define runtime arguments based on your automation use case.
    2. Include required fields such as `name` and `type`.

    ### Step 3: Push changes and build

    1. Commit and push your changes.
    2. Wait until build status is **Completed**.

    ### Step 4: Verify the generated runtime argument form

    1. In Devant, go to the automation **Overview** page, click **Test with Arguments**.

    ### Supported argument types

    | Type | Notes |
    |---|---|
    | `string` | Text input |
    | `number` | Numeric input |
    | `boolean` | Flag-style argument (must include `prefix`) |
    | `enum` | Dropdown selection (requires `values`) |

    !!! note
        Variadic (`string...`-style) input is supported with `repeat: true` for non-boolean types.

    **Runtime argument object fields**

    | Field | Required | Description |
    |----|----|----|
    | `name` | Yes | Unique argument key. Must be a valid identifier. |
    | `type` | Yes | Argument type: `string`, `number`, `boolean`, `enum`. |
    | `displayName` | No | Display label shown in the UI form. |
    | `description` | No | Helper text shown to users in the form. |
    | `required` | No | Whether input is mandatory. Default is `true` (except boolean behavior rules). |
    | `prefix` | No | CLI flag prefix (for example, `--region`, `-D`). Must be unique if used. |
    | `delimiter` | No | Separator between prefix and value: `""`, `"="`, or `":"`. |
    | `values` | Conditional | Required only when `type: enum`. |
    | `repeat` | No | Enables repeated values (`string...` style). Default is `false`. |

    ### Sample component.yaml for HR service automation

    **Use case:** Employee onboarding request automation

    ```yaml
    # +required The configuration file schema version
    schemaVersion: 1.2

    # +optional Incoming connection details for the component
    endpoints: []

    # +optional Outgoing connection details for the component
    dependencies: {}

    # +optional Runtime configurations
    configurations:
      env:
        - name: jiraToken
          valueFrom:
            configForm:
              displayName: Jira API token
              required: true
              type: secret

    # +optional Runtime argument schema
    runtimeArguments:
      - name: employeeName
        displayName: Employee name
        type: string

      - name: employeeId
        displayName: Employee ID
        type: number

      - name: departmentName
        displayName: Department
        type: enum
        values: ["Engineering", "Sales", "HR", "Finance", "Operations"]

      - name: locatedFloor
        displayName: Office floor
        type: enum
        values: ["1","2","3","4"]

      # Must be the last positional argument
      - name: requiredAssets
        displayName: Required assets
        description: Add each requested item such as laptop, monitor, keyboard, mouse.
        type: string
        repeat: true

      - name: sendWelcomeEmail
        displayName: Send welcome email
        type: boolean
        prefix: --send-welcome-email

      - name: priority
        displayName: Ticket priority
        type: number
        prefix: --priority
        delimiter: "="

      - name: notifyGroup
        displayName: Notify group
        type: string
        repeat: true
        prefix: --notify
        delimiter: "="
    ```
    ### Common runtime argument patterns

    === "Boolean flag"
        ```yaml
        - name: enableMonitoring
          displayName: Enable monitoring
          type: boolean
          prefix: --enable-monitoring
        ```
        Result: `--enable-monitoring`

    === "Key-value argument"
        ```yaml
        - name: deployProfile
          displayName: Deploy profile
          type: string
          prefix: --profile
          delimiter: "="
        ```
        Result: `--profile=prod`

    === "Repeated argument"
        ```yaml
        - name: label
          displayName: Label
          type: string
          prefix: --label
          delimiter: "="
          repeat: true
        ```
        Result: `--label=team-a --label=critical --label=backend`

    ### Validation rules

    - `name` must be unique across all runtime arguments.
    - `prefix` (if set) must be unique across all runtime arguments.
    - `values` is required only for `type: enum`; do not define it for other types.
    - `delimiter` can only be `""`, `"="`, or `":"`.
    - Do not define `delimiter` for positional arguments (without `prefix`).
    - Do not define `delimiter` for `boolean` arguments.
    - `boolean` arguments:
        - must include `prefix`,
        - cannot be `required: true`,
        - cannot be `repeat: true`.
    - Only one positional variadic argument is allowed (`repeat: true` without `prefix`).
    - Do not define positional arguments after a positional variadic argument.
    - For positional arguments, required ones must come before optional ones.

    !!! note
        `enum` arguments render as dropdowns and values are validated against the `values` list.

    ### UI behavior
    When a valid runtime argument schema is available, Devant renders typed input fields, enum dropdowns, repeat controls, and pre-execution validation.
    If no schema is available, Devant falls back to generic argument input.

    ### Current limitations
    - Dynamic flag-name generation is not supported (for example, user-defined key names inside `-D<key>=<value>`).
    - Cross-argument dependency validation is not supported (for example, enforcing `--ssl-key` when `--ssl-cert` is provided).
    - Subcommand hierarchies are not supported.
