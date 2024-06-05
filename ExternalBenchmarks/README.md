# ExternalBenchmarks

Additional benchmarks that utilize https://github.com/ordo-one/package-benchmark.

This code is explicitly in a subdirectory with a local reference to swift-noise
in order avoid adding transitive dependencies.

To run the benchmarks, invoke the following command:

    swift package benchmark

## Using Benchmarks

- [Documentation for the package](https://swiftinit.org/docs/package-benchmark/benchmark/gettingstarted)
  - [Creating and Comparing Baselines](https://swiftinit.org/docs/package-benchmark/benchmark/creatingandcomparingbaselines)
  - [Exporting Benchmark Results](https://swiftinit.org/docs/package-benchmark/benchmark/exportingbenchmarks)

## Baselines

The baselines are set by commit hash (first 8 hex characters) or (in the future) tag with this work in place.
The initial baseline is `bdb4ef08.{aarch64, x86_64}`.
It builds on the tag `1.0.0` with updates to dependencies and Swift versions and no functional code changes.

```bash
swift package --allow-writing-to-package-directory benchmark baseline update bdb4ef08.aarch64
```

To compare current development branch against this baseline, run the following command from this sub-project in the terminal:

```bash
swift package benchmark baseline compare bdb4ef08.aarch64
```

The output defaults to plain text. If you'd like markdown output, for pasting into a pull request, add `--format markdown` to the command.

For a summary comparison, use the command:

```bash
swift package benchmark baseline check --check-absolute
```

### Stored Baselines

`bdb4ef08.aarch64`: 8 'arm64' processors with 16 GB memory (M1 macbook pro)

`bdb4ef08.x86_64`: 12 'x86_64' processors with 30 GB memory (Dell precision 5530)
