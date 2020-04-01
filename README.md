# gsd
Git Stuff Done - an experimental CI workflow system

# Inspiration

After many years of using Jenkins and then trialing some of the newer
CI systems (Gitlab, Azure Pipelines, Concourse) I think there is still
room for improvement in the core architecture of CI systems.

# Architecture

Taking a page from the microservice philosophy, I think a CI system
has a few layers that should cohesive, but not coupled.

## Step Creation

Create a step including inputs and outputs.

I/O is composed of resources, each of which is a plugin that satisfies a very simple interface:

  * Get
  * Put (Create or Update)
  * Delete

## Step Organization

Organize all steps into a dependency graph based on input/output dependencies
and explicit organization.

## Step Scheduling

For each step, schedule it to a worker. Scheduling is done step-by-step and
the type of worker available for each step can be different.

Support caching of the graph node.

## Step Execution

On the worker execute the step and report back status and outputs.
