- You are Julian's agent.
- Match the code style and patterns of nearby code by reading it before starting work.
- Never write single-line declaration bodies, even for trivial implementations.
- Make abstractions earn their place. Introduce types when they clarify the model, express ownership, enforce constraints, or provide a useful boundary. Grouping related functions or constants is not sufficient on its own. Keep behavior where it naturally belongs, and prefer structures that make the code easier to understand and use correctly.
- Avoid implicit state machines, such as a collection of properties. Use typed enforcement instead, like enums in Swift.
- Generally, put each type in its own file. Typical exceptions include small, nested or `fileprivate` types.
- Use folders appropriately. For example, contain types in folders like `Models`.
- If you need a tool to complete a task, such as a command-line utility, request_user_input to install it. Avoid choosing a worse tool when a better one could be installed. This rule is for tools installed to my system, not scoped installations like packages or dependencies for a repo/folder.

## Swift Projects

- Follow the Swift API Design Guidelines for code and the Apple Style Guide for copy.
- Prefer native Swift APIs and types. Avoid Objective-C and `NS`-prefixed APIs when suitable Swift alternatives exist.
- Use modern Swift concurrency.
- When creating an Xcode project, always use the new `xcproj` format, replacing `pbxproj`. `pbxproj` should not be used unless it was there before you started working.
- Avoid tuples.
- Prefer methods on the type the behavior belongs to. Avoid global functions, but don’t invent a type solely to avoid a standalone function.
- Avoid `task`, `task(id:`, and `onChange` in SwiftUI. Never use them to "synchronize" state. Instead, layer state appropriately. Avoid multiple sources of truth for state.
- Never use `@unchecked` or `unsafe`.
- Never use `@ObservationIgnored`
- Never use `Binding.init(get:set:)`.
- Never use semicolons.
- Never use antiquated GCD, like locks and semaphores.

## Tests

- Avoid test hooks in non-test code.
- Avoid timeouts or retries in tests.
- Never use sleeps, yields, or any other flaky form of waiting in tests. There are no exceptions to this rule.
- Never write [change-detector tests](https://testing.googleblog.com/2015/01/testing-on-toilet-change-detector-tests.html).
