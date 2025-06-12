# Embabel Agent Framework

![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Apache Tomcat](https://img.shields.io/badge/apache%20tomcat-%23F8DC75.svg?style=for-the-badge&logo=apache-tomcat&logoColor=black)
![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![ChatGPT](https://img.shields.io/badge/chatGPT-74aa9c?style=for-the-badge&logo=openai&logoColor=white)
![Jinja](https://img.shields.io/badge/jinja-white.svg?style=for-the-badge&logo=jinja&logoColor=black)
![JSON](https://img.shields.io/badge/JSON-000?logo=json&logoColor=fff)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-black?style=for-the-badge&logo=sonarqube&logoColor=4E9BCD)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJIDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)

<img align="left" src="https://github.com/embabel/embabel-agent/blob/main/embabel-agent-api/images/315px-Meister_der_Weltenchronik_001.jpg?raw=true" width="180">

&nbsp;&nbsp;&nbsp;&nbsp;

Framework for authoring agentic flows on the JVM that seamlessly mix LLM-prompted interactions
with code and domain models. Supports
intelligent path finding towards goals. Written in Kotlin
but offers a natural usage
model from Java.

## Getting Started

There are two GitHub template repos you can use to create your own project:

- Java template - https://github.com/embabel/java-agent-template
- Kotlin template - https://github.com/embabel/kotlin-agent-template

Or you can use our [project creator](https://github.com/embabel/project-creator) to create a custom project:

```bash
uvx --from git+https://github.com/embabel/project-creator.git project-creator
```

The key repository to explore to learn more is the [Embabel Agent repository](https://github.com/embabel/embabel-agent)

## Key Concepts

Models agentic flows in terms of:

- **Actions**: Steps an agent takes
- **Goals**: What the agent is trying to achieve
- **Conditions**: Conditions to assess before executing an action or determining that a goal has been achieved.
  Conditions are reassessed after each action is executed.
- **Domain model**: Objects underpinning the flow and informing Actions, Goals and Conditions.
- **Plan**: A sequence of actions to achieve a goal. Plans are dynamically formulated by the system, not the programmer.
  The
  system replans after the completion of each action, allowing it to adapt to new information as well as observe the
  effects of the previous action.
  This is effectively an [OODA loop](https://en.wikipedia.org/wiki/OODA_loop).

> Application developers don't usually have to deal with these concepts directly,
> as most conditions result from data flow defined in code, allowing the system to infer
> pre and post conditions.

These concepts deliver the following differentiators versus other agentic systems:

- **Sophisticated planning.** Goes beyond a finite state machine or sequential execution
  with nesting by introducing a true planning step, using a
  non-LLM AI algorithm. This enables the system to perform tasks it wasn’t programmed to do by combining known
  steps in
  a novel order, as well as make decisions about parallelization and other runtime behavior.
- **Superior extensibility and reuse**: Because of dynamic planning, adding more domain objects, actions, goals and
  conditions
  can extend the capability of the system, _without editing FSM definitions._
- **Strong typing and the benefits of object orientation**: Actions, goals and conditions are informed by a domain
  model, which can
  include behavior. Everything is strongly typed and prompts and
  manually authored code interact cleanly. No more magic maps. Enjoy full refactoring support.

Other benefits:

- **Platform abstraction**: Clean separation between programming model and platform concept allow running locally while
  potentially offering higher QoS changing application code.
- **Designed for LLM mixing**: It is easy to build applications that mix LLMs, ensuring the most cost effective yet
  capable solution.
  models. This enables the system to leverage the strengths of different models for different tasks.
- **Built on Spring and the JVM,** making it easy to access existing enterprise functionality and capabilities.
  For example:
    - Spring can inject and manage agents, including using Spring AOP to decorate functions.
    - Robust persistence and transaction management solutions are available.
- **Designed for testability** from the ground up. Both unit testing and agent end to end testing are easy.

Flows can be authored in one of two ways:

- Annotation-based model similar to Spring MVC, with types annotated with `@Agent` with `@Goal`, `@Condition` and
  `@Action` methods.
- Kotlin DSL.

Either way, flows are backed by a domain model of objects that can defined behavior.
