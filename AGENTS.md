- You are Julian's agent.
- Match the code style and patterns of nearby code by reading it before starting work.
- Never write single-line declaration bodies, even for trivial implementations.
- Make abstractions earn their place. Introduce types when they clarify the model, express ownership, enforce constraints, or provide a useful boundary. Grouping related functions or constants is not sufficient on its own. Keep behavior where it naturally belongs, and prefer structures that make the code easier to understand and use correctly.
- Avoid implicit state machines, such as a collection of properties. Use typed enforcement instead, like enums in Swift.
- Generally, put each type in its own file. Typical exceptions include small, nested or `fileprivate` types.
- Use folders appropriately. For example, contain types in folders like `Models`.
- If you need a tool to complete a task, such as a command-line utility, request_user_input to install it. Avoid choosing a worse tool when a better one could be installed. This rule is for tools installed to my system, not scoped installations like packages or dependencies for a repo/folder.
- Use `gt pr create` without `--agit` to create regular branch-based Gitea PRs. For stacks, keep branches in the same repository and set `--base` to the parent PR’s head branch.

## Swift Projects

- Follow the Swift API Design Guidelines for code and the Apple Style Guide for copy.
- Prefer native Swift APIs and types. Avoid Objective-C and `NS`-prefixed APIs when suitable Swift alternatives exist.
- Use modern Swift concurrency.
- When creating an Xcode project, always use the new `xcproj` format, replacing `pbxproj`. `pbxproj` should not be used unless it was there before you started working.
- Use Xcode’s file-system synchronized groups (buildable folders) for source directories in `project.xcproj`, represented by `"kind": "folder"` with folder-level target membership. Let Xcode discover their contents instead of maintaining explicit file lists. Add individual file references or membership overrides only when needed for exceptions.
- Avoid tuples.
- Prefer methods on the type the behavior belongs to. Avoid global functions, but don’t invent a type solely to avoid a standalone function.
- Never use `@unchecked` or `unsafe`.
- Never use semicolons.
- Never use antiquated GCD, like locks and semaphores.

## SwiftUI

- Avoid `task`, `task(id:`, and `onChange` in SwiftUI. Never use them to "synchronize" state. Instead, layer state appropriately. Avoid multiple sources of truth for state.
- Keep view initializers cheap. Preserve deferred initialization for private `@State`-owned objects instead of eagerly constructing models or native views whenever a view value is recreated.
- Factor independently updating UI sections into separate `View` types with explicit inputs. Computed view properties and `@ViewBuilder` helpers do not create independent update boundaries; reserve them for small fragments without that need.
- Keep view inputs and observation dependencies narrow. Pass only the value-type fields a view needs, and avoid coupling unrelated UI to one aggregate observed property. Preserve state invariants and a single source of truth when changing its shape.
- Prefer `Equatable` for value types stored in `@Observable` models when equality is meaningful, so unchanged assignments can avoid unnecessary observation updates.
- Never use `@ObservationIgnored`
- Never use `Binding.init(get:set:)`.
- Use `@Entry` for custom environment, focused, transaction, and container values when supported by the deployment target, instead of handwritten key types and accessors. Ensure defaults remain stable across reads.
- Do not store closures or function values in custom environment or focused values, including inside wrapper types. Pass stable data or model references and expose actions as methods. Framework-provided action types are exempt.

## Tests

- Avoid test hooks in non-test code.
- Avoid timeouts or retries in tests.
- Never use sleeps, yields, or any other flaky form of waiting in tests. There are no exceptions to this rule.
- Never write [change-detector tests](https://testing.googleblog.com/2015/01/testing-on-toilet-change-detector-tests.html).
