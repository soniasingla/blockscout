# Contribution Guidelines: What We Are Looking For

We welcome contributions that enhance the project and improve the overall quality of our codebase. While we appreciate the effort that goes into making contributions, we kindly ask that contributors focus on the following types of changes:
- Feature Enhancements: Substantial improvements or new features that add significant value to the project.
- Bug Fixes: Fixes for known bugs or issues that impact functionality.
- Documentation Improvements: Comprehensive updates to documentation that clarify usage, installation, or project structure.
- Performance Improvements: Changes that enhance the performance or efficiency of the application.

# Contributing

1. Fork it ( <https://github.com/blockscout/blockscout/fork> )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Write tests that cover your work
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request. The title of Pull Request should follow [Conventional Commits specification](https://www.conventionalcommits.org/en/v1.0.0/) and should start with `feat:`, `fix:`, `chore:`, `doc:`, `perf:`, `refactor:` prefix.

## General

* Commits should be one logical change that still allows all tests to pass.  Prefer smaller commits if there could be two levels of logic grouping.  The goal is to allow contributors in the future (including your own future self) to determine your reasoning for making changes and to allow them to cherry-pick, patch or port those changes in isolation to other branches or forks.
* If during your PR you reveal a pre-existing bug:
  1. Try to isolate the bug and fix it on an independent branch and PR it first.
  2. Try to fix the bug in a separate commit from other changes:
     1. Commit the code in the broken state that revealed the bug originally
     2. Commit the fix for the bug.
     3. Continue original PR work.

## Enhancements

Enhancements cover all changes that make users lives better:

* [feature requests filed as issues](https://github.com/blockscout/blockscout/labels/enhancement) that impact end-user [contributors](https://github.com/blockscout/blockscout/labels/contributor) and [developers](https://github.com/blockscout/blockscout/labels/developer)
* changes to the [architecture](https://github.com/blockscout/blockscout/labels/architecture) that make it easier for contributors (in the GitHub sense), dev-ops, and deployers to maintain and run blockscout

## Bug Fixes

For bug fixes, whenever possible, there should be at least 2 commits:

1. A regression test commit that contains tests that demonstrate the bug and show as failing.
2. The bug fix commit that shows the regression test now passing.

This format ensures that we can run the test to reproduce the original bug without depending on the new code in the fix, which could lead to the test falsely passing.

## Incompatible Changes

Incompatible changes can arise as a side-effect of either Enhancements or Bug Fixes.  During Enhancements, incompatible changes can occur because, as an example, in order to support showing end-users new data, the database schema may need to be changed and the index rebuilt from scratch.  During bug fixes, incompatible changes can occur because in order to fix a bug, the schema had to change, or how certain internal APIs are called changed.

* Incompatible changes should be called out explicitly, with any steps the various user roles need to do to upgrade.
* If a schema change occurs that requires a re-index add the following to the Pull Request description:

  ```markdown
  **NOTE**: A database reset and re-index is required
  ```

## Pull Request

There is a [PULL_REQUEST_TEMPLATE.md](PULL_REQUEST_TEMPLATE.md) for this repository, but since it can't fill in the title for you, please follow the following steps when opening a Pull Request before filling in the template:

* [ ] Title
  * [ ] Prefix labels if you don't have permissions to set labels in the GitHub interface.
  * (bug) for [bug](https://github.com/blockscout/blockscout/labels/bug) fixes
  * (enhancement) for [enhancement](https://github.com/blockscout/blockscout/labels/enhancement)s
  * (incompatible changes) for [incompatible changes](https://github.com/blockscout/blockscout/labels/incompatible%20changes), such a refactor that removes functionality, changes arguments, or makes something required that wasn't previously.
  * [ ] Single sentence summary of change
    * What was fixed for bugs
    * What was added for enhancements
    * What was changed for incompatible changes

See [#255](https://github.com/blockscout/blockscout/pull/255) as an example PR that uses GitHub keywords and a Changelog to explain multiple changes.

## Basic Naming Convention

When contributing to the codebase, please adhere to the following naming conventions to ensure clarity and consistency:

- Use full names for entities. Avoid abbreviations or shorthand.
  - Instead of "tx" or "txn", use "transaction".
  - Instead of "txs", use "transactions".
  - Instead of "tx_hash" or "txn_hash", use "transaction_hash".
  - Instead of "block_num", use "block_number".
- Ensure that variable names are descriptive and convey the purpose or content clearly.
- Consistent naming helps in maintaining readability and understanding of the code, especially for new contributors.

By following these conventions, we can maintain a clean and understandable codebase.

### API V2 Naming Convention

When contributing to the API v2, please adhere to the following naming conventions for response fields to ensure clarity and consistency:

- The block number should be returned as a number in the `block_number` property.
- The transaction hash should be returned as a hex string in the `transaction_hash` property.
- All fields that contain the "index" suffix should be returned as numbers.

## Compile time Environment Variables

When working with compile time environment variables in the codebase, follow these guidelines:

- Always use the `Utils.CompileTimeEnvHelper` module instead of direct `Application.compile_env/2` calls:

```elixir
# DO use this approach
use Utils.CompileTimeEnvHelper,
    attribute_name: [:app, :test]

# Access the value using the module attribute
@attribute_name

# DON'T use this approach
Application.compile_env(:app, :test)  # avoid direct compile_env calls
```

This approach provides faster compilation time and simplifies development and maintenance.

