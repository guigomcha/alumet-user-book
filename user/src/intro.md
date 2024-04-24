# Introduction

Welcome to the ALUMET user/admin guide!
If you want to measure something with ALUMET, you have come to the right place.

## What is ALUMET?

ALUMET is a software project that provides a "measurement pipeline" that is:
- **Generic**: You can plug many different sources, outputs, and even transformation functions into Alumet.
- **Extensible**: Alumet is made of a core, on top of which we add plugins. You choose the plugins that suit your needs and build a measurement application with them. You can also create new plugins with an easy-to-use, high-level API.
- **Lightweight and fast**: Alumet is written in Rust and optimized for minimal latency and low memory consumption. Furthermore, many plugins are based on low-level sensors like the [perf_events interface](https://man.archlinux.org/man/perf_event_open.2.fr) of the Linux kernel.
- **Adaptive**: Unlike other measurement tools, Alumet allows the pipeline to be reconfigured on-the-fly. Thanks to our novel approach, you can switch from monitoring at 1 Hz to profiling at 1000 Hz without restarting anything!
- **Rigorous**: The project is based on active research work, involving both  academia and industry.

To summarize, ALUMET means _Adaptive, Lightweight, Unified METrics_.
