# Blyx Wren

Run named checks and skips, compare floating-point measurements, and report a TAP 13 stream and a process exit status for CI.

This extension includes the Blyx Wren 0.1.0 source, a runnable example and completions for its public functions. It uses the Blyx Language extension for syntax highlighting and execution.

## Run in the editor

1. Open an empty file named `wren-demo.blyx`.
2. Type `blyx-wren-demo` and select **Wren — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
3
1
1
1
```

## Use Wren in a project

Extract the starter into a new folder. It contains `main.blyx`, the licensed framework source in `vendor/wren`, and a VS Code task. With the Blyx 0.2.1 compiler and host toolchain installed, run `blyxc native-run main.blyx` from that folder. Type `blyx-wren-` in a Blyx file to see the framework completions. [Download the starter ZIP](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-wren-starter-0.1.0.zip)

[API and input requirements](https://www.blyx-lang.space/packages/wren) · [Framework source](https://github.com/Rahulchaube1/blyx-wren/tree/54face061805e7bf749c500aa31b3341eee91b4b) · [Report an issue](https://github.com/Rahulchaube1/blyx-wren/issues)

[GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) · [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube)
