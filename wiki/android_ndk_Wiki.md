# SigmaOS-android-ndk Component Wiki

## Overview
SigmaOS-android-ndk provides Android NDK support and native development kit integration for the SigmaOS operating system. It demonstrates the native development subsystem and NDK integration within the SigmaOS ecosystem, following the principles of clear abstraction and deterministic NDK initialization.

## Principles
- Single Responsibility
- NDK Abstraction
- Fail-Fast on NDK Initialization Errors
- Deterministic NDK Setup
- Clear Abstraction Over NDK APIs
- Composition over Inheritance for NDK extensions

## Architecture
SigmaOS-android-ndk follows an NDK pattern:
- **NDK Core**: Provides native development kit support, native library management, and NDK build integration
- **Native Library**: Supports native libraries, native asset management, and native module loading
- **Build Integration**: Supports NDK build, native compilation, and NDK toolchain integration
- **Error Handling**: Fail-fast on invalid NDK configurations or unsupported NDK types

## API
The component provides the following public APIs:
- `ndk::library::load(path)` - Load a native library by given path
- `ndk::module::register(module)` - Register a native module by given name
- `ndk::build::compile(path)` - Compile native code by given path
- `ndk::status::ndk()` - Get NDK status and NDK availability
- Error types for NDK failure scenarios or unsupported NDK types

## Test Structure (Arrange-Act-ASSERT)
All tests follow the AAA pattern:
1. **Arrange**: Set up test environment with specific NDK configuration
2. **Act**: Execute the code under test (library loading, module registration)
3. **Assert**: Verify the expected NDK results

Example:
```rust
#[test]
fn test_ndk_library_aaa() {
    // Arrange
    let library_path = "/libs/native-lib.so";
    
    // Act
    let result = ndk::library::load(library_path);
    
    // Assert
    assert!(result.is_ok());
    let loaded = result.unwrap();
    assert!(loaded.is_loaded());
}
```

## Development
- Follows Rust best practices with `#![forbid(unsafe_code)]`
- NDK initialization is best-effort; gracefully degrades on unsupported configurations
- Comprehensive error types for all NDK failure scenarios
- Unit tests provided for library loading and module registration
- Integration tests for full NDK system with actual NDK integration

## TODO
- Add support for additional NDK features (NDK APIs, NDK toolchains, NDK debug)
- Expand native library capabilities (native assets, native modules, native bindings)
- Add build features (NDK build, native compilation, NDK toolchain integration)
- Create integration tests with actual NDK systems and NDK integration
- Implement NDK persistence and NDK state management