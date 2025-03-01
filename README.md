# mcpx-eval

A framework for evaluating open-ended tool use across various large language models.

`mcpx-eval` can be used to compare the output of different LLMs with the same prompt for a given task using [mcp.run](https://www.mcp.run) tools.
This means we're not only interested in the quality of the output, but also curious about the helpfulness of various models
when presented with real world tools.

## Tests

The [tests/](https://github.com/dylibso/mcpx-eval/tree/main/tests) directory contains pre-defined tests

## Installation

```bash
uv tool install git+https://github.com/dylibso/mcpx-eval
```

## Usage

Run the `my-test` test for 10 iterations:

```bash
mcpx-eval test --model ... --model ... --config my-test.toml --iter 10
```

Generate an HTML scoreboard for all tests:

```bash
mcpx-eval gen --html results.html --show
```

### Test file

A test file is a TOML file containing the following fields:

- `name` - name of the test
- `prompt` - prompt to test, this is passed to the LLM under test
- `check` - prompt for the judge, this is used to determine the quality of the test output 
- `expected-tools` - list of tool names that might be used
- `max-tool-calls` - optional, limits the maximum number of tool calls before raising an error
- `import` - includes fields from another test TOML file
