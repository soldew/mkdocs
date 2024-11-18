DocProStar processes consist of activities [[Activity routing|connected by routes]]. Activities can be classified in one of several types depending on how they are started, and are classified as such in the Process Modeler's "Activities" mode.

A process consists of activities connected with routes. Depending on how an activity is started, activities are listed within one of the following areas within the main panel.

## Time-driven activity

Time-driven activities are started by a timer, and perform their implementation only when a timer notifies it for execution. 

For more details on how to set timers for such activities, see the [[Timer Settings]] article.

## Document-driven activity

A document-driven activity picks up the work items when they become available such as for example when a specified folder contains one or more document files. The activity executes the implementation and moves the work item in the process flow.

## Event-driven activities

Event-driven activities are used to feed the platform from an external system to perform document processing.

## External activities

An external activity is a third-party implementation that uses the application programming interface to access and process work items in an external desktop or Web client application, such as Document Review and Batch Review.

## System
These are special activities categorized by their function and other functionality are activities, such as the Process Starter. The process starter activity is used to trigger sub-processes.

## System Agents

The System Agents area provides a list of available system agents. Unlike activities that are added at a specific position in your process flow, you can add a system agent to a process to monitor the process for work items in general. For example, the Deletion System Agent removes all work items from the process that have been marked for deletion and have reached their expiration date. 

Other system agents allow to monitor one or more activities for work items that are in Error state, to either move them to a different activity or to set their status back to Ready, for example to restart processing after a database lookup ran into an time out