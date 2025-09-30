# am-tests

A testing library for the AM programming language that provides assertion utilities for unit testing.

## Overview

`am-tests` is a library that provides a comprehensive set of assertion functions for testing AM language applications. It includes various assertion methods to validate expected behavior in your tests.

## Features

- **Equality assertions**: Check if values are equal
- **Boolean assertions**: Verify true/false conditions
- **Null assertions**: Validate null and non-null values
- **Failure assertions**: Explicitly fail tests with custom messages
- **Exception handling**: All assertions throw `AssertException` when they fail

## Installation

Add `am-tests` as a dependency in your `package.yml`:

```yaml
dependencies:
  - id: am-tests
    realm: github
    type: git-repo
    tag: latest
    branch: master
    url: https://github.com/anderskjeldsen/am-tests.git
```

## Usage

Import the testing namespace in your test files:

```aml
import Am.Tests

class MyTests {
    test myTestMethod() {
        Assert.assertEquals(5, 5)
        Assert.assertTrue(true)
        Assert.assertNotNull("value")
    }
}
```

## API Reference

### Assert Class

The `Assert` class provides static methods for making assertions in your tests:

#### `assertEquals(expected: Any, actual: Any)`
Asserts that two values are equal.

```aml
Assert.assertEquals(5, 5)
Assert.assertEquals("hello", "hello")
```

#### `assertTrue(condition: Bool)`
Asserts that a condition is true.

```aml
Assert.assertTrue(true)
Assert.assertTrue(5 > 3)
```

#### `assertFalse(condition: Bool)`
Asserts that a condition is false.

```aml
Assert.assertFalse(false)
Assert.assertFalse(5 < 3)
```

#### `assertNotNull(value: Any?)`
Asserts that a value is not null.

```aml
Assert.assertNotNull("not null")
Assert.assertNotNull(someObject)
```

#### `assertNull(value: Any?)`
Asserts that a value is null.

```aml
Assert.assertNull(null)
Assert.assertNull(optionalValue)
```

#### `fail(message: String)`
Explicitly fails a test with a custom message.

```aml
Assert.fail("This should not happen")
```

### AssertException

All assertion failures throw an `AssertException`. You can catch these exceptions to test assertion failures:

```aml
var error = true
try {
    Assert.assertEquals(5, 4)
} catch (e: AssertException) {
    error = false
}
Assert.assertEquals(false, error)
```

## Example

See the `tests/AssertTests.aml` file for comprehensive usage examples:

```aml
namespace Tests {
    class AssertTests {
        import Am.Lang
        import Am.Tests

        test testAssertEquals() {
            Assert.assertEquals(5, 5)
        }

        test testAssertTrue() {
            Assert.assertTrue(true)
        }

        test testAssertFalse() {
            Assert.assertFalse(false)
        }

        test testAssertNotNull() {
            Assert.assertNotNull("not null")
        }

        test testAssertNull() {
            Assert.assertNull(null)
        }
    }
}
```

## Building

The project uses the AM language build system. Build targets are defined in `package.yml`:

- **macOS**: Build for macOS platform
- **Linux x64**: Build for Linux x64 platform

## Dependencies

- [am-lang-core](https://github.com/anderskjeldsen/am-lang-core): Core AM language library

## License

See the repository license for details.

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.
