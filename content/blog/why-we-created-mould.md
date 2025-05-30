+++
title = "Why We Created Mould"
date = 2025-06-03
+++

Mould was born to improve the success rate of software releases.

In the software development process, releasing a new version typically involves multiple environments: testing, staging (though some companies may not have this), and production. Each release requires executing many operations across these environments, most of which are not automated. Instead, they are manually performed by operations teams. The success of these updates depends on both the attentiveness of the operations personnel and the accuracy of the release documentation.

While we can generally trust the diligence of the operations team, the correctness of the release documentation is far less reliable. Typically, this documentation is a manual describing a series of steps—such as updating application versions, executing database SQL scripts, modifying environment configurations, starting or stopping scheduled tasks, and restarting applications. These steps are difficult to automate due to a lack of standardization, and standardization is a prerequisite for automation. As a result, these procedures are usually documented manually. When the system is complex with numerous subsystems, this documentation becomes extremely convoluted, making a smooth release far from easy.

The situation worsens when a company lacks a staging environment. Without a trial run, the operations team must update production directly after testing, working from unfamiliar documentation with no room for error. A single mistake can lead to a release failure, and the entire process can take anywhere from several dozen minutes to several hours.

Tools like Jenkins offer some automation, but Jenkins is more focused on continuous integration than continuous deployment. It operates on the concept of "projects" rather than "environments." To execute a single task across multiple environments, multiple projects must be created and manually kept in sync—including both the tasks themselves and their associated variables. Creating or modifying projects for every release is impractical. Jenkins tightly couples tasks with environments, making it difficult to switch contexts seamlessly.

Mould addresses this by standardizing operational steps (changes to resource states) to decouple tasks (collections of steps) from environments (collections of resources). This separation enables tasks to be executed across different environments. The ultimate goal is to empower operations teams to take a pre-validated task list, select their managed environment, and execute it with a single click—achieving one-click deployment. The operations team only needs to prepare resources and configure connection parameters (a mostly one-time effort), then select the environment and trigger execution whenever a task is ready.

Since different companies use different technologies, the types of resources in their environments vary. Standardizing all resource types is unrealistic, so Mould introduces an extensible plugin mechanism. By defining extension interfaces, companies can implement custom plugins to fit their specific needs. We will also provide extensions for commonly used resources.

To learn more about Mould’s architecture and core concepts, stay tuned for our next article.