# Why ALUMET and not \<X\>?

Every tool comes with its limitations, and Alumet is not the only measurement software out there. Here is why we think that Alumet may be better than other existing tools.

## Generic and Unified

You can plug many different sources, outputs, and even transformation functions into Alumet, without modifying its core. Instead of having one specialized tool for the CPU, another one for the GPU, and another one for Kubernetes pods, each with a different interface, polling frequency and methodology, you can have one instance Alumet.

With Alumet, the tedious work that was previously duplicated is now factorized in a common tool. Tedious work for the administrator: configuring the gathering of the metrics, giving the proper rights to each tool, saving the results to a database, etc. But also tedious work for the developer: supporting a new database, writing the configuration management code, optimizing each tool, etc.

## Extensible

Alumet is made of a core, on top of which we add plugins. You choose the plugins that suit your needs and build a measurement application with them. You can also create new plugins with an easy-to-use, high-level API.

Some existing tools claim that they have a plugin interface and a modular code. However, their modularity is often limited to a few functions or abstract interfaces in a largely monolithic codebase. For example, supporting a new source of measurements often require to modify the core of the tool. In contrast, Alumet offers modularity in a way that is both easy to use _and_ powerful. The first evidence of this advantage is that the core and the plugins are in distinct crates, rather than in a monolithic codebase. A second evidence is that Alumet plugins have less restrictions than Telegraf plugins. For instance, the same Alumet plugin can provide sources, transforms and outputs. A plugin can also modify the pipeline's configuration at runtime, without prior knowledge of the other plugins.

## Lightweight and fast

Alumet is written in Rust and optimized for minimal latency and low memory consumption. Furthermore, many plugins are based on low-level sensors like the [perf_events interface](https://man.archlinux.org/man/perf_event_open.2.fr) of the Linux kernel. Finally, the plugin system allows you to only include the plugins that suit your needs, instead of installing a do-it-all monolith.

Our preliminary results seem to show that Alumet uses less CPU cycles, consumes less memory and is overall more efficient than the existing tools. We will upload benchmark results in the future.

## Adaptive

We worked hard to provide two forms of adaptation:
1. Adapting to your needs at compile-time: Thanks to Alumet's modularity, you are able to build a measurement software tailored to your needs.
2. Adaptings to the context at run-time: Unlike other tools, Alumet allows the pipeline to be reconfigured on-the-fly. With our novel approach, you can switch from monitoring at 1 Hz to profiling at 1000 Hz without restarting anything.

## Rigorous

Finally, the project is based on active research work, involving both academia and industry. One of our goals is to overcome the limitations and mistakes that we found in the other tools. We want to produce a robust tool that will offer accurate measurements in different contexts, such as CS research, HPC clusters and Cloud services.

People at BULL SAS (part of Eviden) and the LIG (Grenoble's laboratory of computer science) are working on Alumet.
