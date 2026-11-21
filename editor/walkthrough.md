## Count passes, failures and skips

Start with wr_begin, pass the returned suite to each check or skip, then call process_exit(wr_end(suite)). The producer emits a trailing TAP plan. Names are truncated at a line break or # to keep the stream unambiguous. Relative tolerance ranges from zero to one. Inputs for measurements and tolerances must be finite.

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

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-wren)
