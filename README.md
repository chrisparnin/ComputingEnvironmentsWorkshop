[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) | [Baker](Baker.md)

Computing Environment Workshop
----------------------------------

The goal of this workshop is to demonstrate the value of automatically creating computing environments. At the end of this workshop, you should be able to understand how to configure and automatically create a virtual machine for programming tasks.

### Not Your Typical Virtual Machine

> Computing environments are for *running* code, not *writing* code.

When developers think about virtual machines, a common idea that comes to mind is a dedicated heavy-weight virtualized system with a full graphics Desktop. Alternatively, you may think of dual-booted systems. While these types of systems can be useful, the goal of this workshop is to introduce you to a different concept for software development.

We define a *computing environment* as an automatically configured environment for executing a program and interfacing with its data and infrastructure components. Computing environments are useful for personal software development that involves data analytics, machine learning, or requires complex infrastructure. However, using computing environments have other benefits, such as supporting configuration management for software development teams, reproducibility for research, and enabling scaling of computations as necessary. 

To use a computing environment, you can use your host operating system to write code, interact with the running program, and visualize its executions. But the code itself runs in a headless virtual machine. To accomplish this, we use a set of tools to enable you to map files and program between your host environment and computing environment.

### Workshop

1. We start with learning some tools that streamline the process of [creating virtual machines](VM.md).
2. We practice [using several computing environments](CE.md).
3. We demonstrate using [baker](Baker.md).
4. Advanced topics (TBA).
