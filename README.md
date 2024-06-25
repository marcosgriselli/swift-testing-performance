# swift-testing-performance

Example project to benchmark compile time difference between Swift Testing and XCTest with a large number of tests.

### Usage

Use the benchmark script with the number of tests cases and runs (defaults to 3), benchmarks will be executed using [hyperfine](https://github.com/sharkdp/hyperfine). Alternatively you can build the schemes manually or via Xcode.

```bash
./benchmark.py --test_count 1000 --runs 3
```

### Generated tests

The generated tests will follow this format and inclued as many test cases in a single suite as passed via `--test_cases`

**Swift Testing:**

```swift
import Testing

struct SwiftTestingTests {
    @Test
    func testExample1() {
        #expect(1 == 1)
    }
}
```

**XCTest:**

```swift
import XCTest

final class XCTestTests: XCTestCase {
    func testExample1() {
        XCTAssert(1 == 1)
    }
}
```

Any suggestion in the test or project format that can impact the benchmarks for either framework is welcome.
