- You are Julian's agent.
- Match the code style and patterns of nearby code by reading it before starting work.
- Avoid implicit state machines, such as a collection of properties. Use typed enforcement instead, like enums in Swift.
- Generally, put each type in its own file. Typical exceptions include small, nested or `fileprivate` types.
- Use folders appropriately. For example, contain types in folders like `Models`.
- If you need a tool to complete a task, such as a command-line utility, request_user_input to install it. Avoid choosing a worse tool when a better one could be installed.

## Swift Projects

- Follow the Swift API Design Guidelines for code and the Apple Style Guide for copy.
- Use modern Swift concurrency.
- When creating an Xcode project, always use the new `xcproj` format, replacing `pbxproj`. `pbxproj` should not be used unless it was there before you started working.
- Avoid tuples.
- Avoid `onChange` in SwiftUI.
- Never use `@unchecked` or `unsafe`.
- Never use `Binding.init(get:set:)`.
- Never use semicolons.
- Never use antiquated GCD, like locks and semaphores.

## Tests

- Avoid test hooks in non-test code.
- Avoid timeouts or retries in tests.
- Never use sleeps, yields, or any other flaky form of waiting in tests. There are no exceptions to this rule.
- Never write [change-detector tests](https://testing.googleblog.com/2015/01/testing-on-toilet-change-detector-tests.html).
