+++
title = "The Architecture of Mould"
date = 2025-06-04
+++

An environment consists of a set of resources, where each resource is defined by an extension and acts as an instance of that extension. The collection of all extensions corresponding to an environment’s resources forms the environment schema (also called a template or class). The schema is an abstraction of the environment, while the environment itself is an instance of that schema.

A task list is composed of multiple steps, each targeting an extension within the environment schema. Extension authors define both the configuration parameters required for a resource and the possible change operations that can be performed on it. Task steps can only select from these predefined operations and supply the necessary parameters. This means the task list operates on the environment schema rather than a specific environment instance—achieving decoupling.

When a task list is executed, it must be provided with an environment instance as its sole parameter. The actual updates to the environment are then carried out programmatically by the predefined behaviors of the extensions, eliminating the need for manual intervention by operations teams.

The environment schema acts like a mould, constraining every task list that modifies the environment to ensure consistency across different environments. This is why the tool is named Mould—it aims to produce identical "products" (environments) just as a physical mould does. This greatly reduces discrepancies between environments, lowers system complexity, and results in fewer bugs.

Standardization also brings an additional benefit: reduced execution time. If the operations are not inherently performance-intensive, the entire process can complete in seconds or even tens of seconds, significantly shortening deployment times.

That said, not all resources are easy to standardize. For example, modifying Nginx configuration files is complex and thus harder to standardize—which is why Mould does not yet include an Nginx extension. On the other hand, well-structured data formats like JSON and properties files (simple key-value pairs) are much easier to standardize.

Would you like any refinements or additional details in certain sections?