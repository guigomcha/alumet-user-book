# Start here - Installing Alumet

> ⚠️&nbsp;&nbsp;**Alumet is currently in Beta**.
>
> If you have trouble using Alumet, do not hesitate to [discuss with us](https://github.com/alumet-dev/alumet/discussions), we will help you find a solution.
> If you think that you have found a bug, please [open an issue](https://github.com/alumet-dev/alumet/issues) in the repository.

For the moment, the only way to use Alumet is to download its sources and to compile it (see below).
We intend to provide easy-to-use packages in the future.

## Compiling from source

**Prerequisite**: you need to [install the Rust toolchain](https://rustup.rs/).

Open a Terminal and download the repository:

```sh
git clone https://github.com/alumet-dev/alumet.git
```

The Alumet repository contains multiple crates ("crates" are Rust libraries/packages).
To run Alumet, we are interested in `app-agent`, which produces a runnable measurement tool by compiling the core of Alumet and a set of standard plugins into a single binary.

Let's compile and run this agent.
```sh
cd alumet/app-agent
cargo run -- --help
```

Here, we use `cargo run` to compile and run the agent. The double dash (`--`) allows to pass arguments to the agent, here `--help`.

You should get something like this:
```
$ cargo run -- --help
   Compiling tokio v1.37.0
   ...
   Compiling app-agent v0.4.0 (/home/user/alumet/app-agent)
    Finished dev [unoptimized + debuginfo] target(s) in 18.07s
     Running `/home/user/alumet/target/debug/alumet-agent --help`
[2024-05-14T17:58:00Z INFO  alumet_agent] Starting ALUMET agent v0.4.0
Command line arguments

Usage: alumet-agent [OPTIONS] [COMMAND]

Commands:
  run           Run the agent and monitor the system
  exec          Execute a command and observe its process
  regen-config  Regenerate the configuration file and stop
  help          Print this message or the help of the given subcommand(s)

Options:
      --max-update-interval <MAX_UPDATE_INTERVAL>
          Maximum amount of time between two updates of the sources' commands.
          
          A lower value means that the latency of source commands will be lower, i.e. commands will be applied faster, at the cost of a higher overhead.

  -h, --help
          Print help (see a summary with '-h')
```

To run the agent, you can use the `run` command.
```sh
cargo run -- run
```

Alumet will then start to observe your machine.

## Output file and configuration

With the standard set of plugins, the measurements are saved in a CSV file.
By default, this is `alumet-output.csv`. You can change this by editing `alumet-config.toml`. Note that the configuration file is automatically created by Alumet if it does not exist.

[Learn more about Alumet's config here](./config.md).

## Tips

### Default command

Since `run` is the default command, you can also run the agent without any argument.
```sh
cargo run
```

### Path to the binary

The binary produced by `cargo` is located, when building with a default target (which links to libc) and for the host architecture, at:
- `../target/debug/alumet-agent` in debug mode
- `../target/release/alumet-agent` in release mode

The aforementioned paths are relative to the `app-agent` directory.

### Release mode

By default, the measurement tool is built in _debug mode_, which enables better diagnostics but disables many optimizations.
To deploy Alumet "in production", you would want to use the _release mode_ by adding `--release` to the cargo flags:
`cargo run --release` (to run the agent now) or `cargo build --release` (to produce the binary and stop).
