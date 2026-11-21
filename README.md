<img src="assets/logo.png" width="112" height="112" alt="A chestnut wren with a cream eyebrow holds its striped tail upright.">

# Blyx Wren

Run named checks and skips, compare floating-point measurements, and report a TAP 13 stream and a process exit status for CI.

A test that only prints an error can leave a build green. TAP defines a machine-readable result for each check and a plan stating how many results to expect. Wren couples that output to the number of failures. [Test Anything Protocol, TAP 13 specification](https://testanything.org/tap-version-13-specification.html)

## Editor extension

Install **RahulChaube.blyx-wren** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-wren-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/wren#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-wren-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-wren-starter-0.1.0.zip)

## Install and run

Install the Blyx 0.2.1 compiler and a Rust toolchain with a host linker. Clone the versioned release, then run its small example and regression suite.

```sh
cargo install --locked --version 0.2.1 blyxc
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-wren.git
cd blyx-wren
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

Expected output from the small example

```text
3
1
1
1
```

## Test an invoice and packing calculation

The suite checks a decimal invoice total and a whole-box count, then records an offline printer as a skip. Change the expected box count to see the process exit with status 1.

```sh
blyxc native-run project.blyx
```

Project output

```text
TAP version 13
ok 1 - decimal invoice total
ok 2 - full boxes in a shipment
ok 3 - label printer # SKIP device offline
1..3
```

[Run the portable example in the browser](https://www.blyx-lang.space/play?example=package-wren) · [Follow the handbook exercise](https://doc.blyx-lang.space/guide/wren) · [Download the release](https://github.com/Rahulchaube1/blyx-wren/releases/tag/v0.1.0)

## Use the framework in your own project

From the folder containing your entry file, clone the release into `vendor/wren`.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-wren.git vendor/wren
```

```blyx
use vendor::wren::wren;

fn main() {
    let first = wr_record(wr_start(), wr_near(0.1 + 0.2, 0.3, 0.000001, 0.0), false);
    let second = wr_record(first, false, true);
    let result = wr_record(second, 2 * 2 == 5, false);
    println!(at(result, 0));
    println!(at(result, 1));
    println!(at(result, 2));
    println!(wr_exit(result));
}
```

Run `blyxc native-run main.blyx`. For the complete native workflow also import `use vendor::wren::tap;`.

Start with wr_begin, pass the returned suite to each check or skip, then call process_exit(wr_end(suite)). The producer emits a trailing TAP plan. Names are truncated at a line break or # to keep the stream unambiguous. Relative tolerance ranges from zero to one. Inputs for measurements and tolerances must be finite.

| API | Behavior |
| --- | --- |
| `wr_begin(), wr_check(suite, passed, label)` | Import tap. Start a TAP stream and record numbered checks. |
| `wr_skip(suite, label, detail), wr_end(suite)` | Declare a skip and finish with a plan. wr_end returns 1 when a check failed. |
| `wr_near(actual, expected, absolute, relative)` | Compare using the larger of an absolute tolerance and a tolerance scaled by the larger input magnitude. |
| `wr_start(), wr_record(suite, passed, skipped), wr_exit(suite)` | Track total, failed and skipped cases without writing TAP output. |

## Contribute

When opening an issue, include the smallest reproducing Blyx input, the compiler version and the output you expected. [Source and issues](https://github.com/Rahulchaube1/blyx-wren/issues) · [Blyx community](https://www.blyx-lang.space/community)

Dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
