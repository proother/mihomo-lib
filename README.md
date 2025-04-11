# Mihomo Universal Binaries

A collection of precompiled [Mihomo](https://github.com/MetaCubeX/mihomo) universal binaries for multiple platforms. This repository automates the creation of multi-architecture binaries for macOS, Windows, and Android.

## Overview

### What is Mihomo?
**Mihomo** is a powerful and versatile proxy platform maintained by the [MetaCubeX](https://github.com/MetaCubeX) community. Formerly known as Clash.Meta, it offers advanced traffic management, encryption, and routing capabilities.

### Available Builds
This repository provides precompiled universal binaries for multiple platforms:

1. **mihomo-darwin-universal** - Universal binary for macOS (arm64 + amd64)
2. **mihomo-windows-all** - Package containing binaries for all Windows architectures (amd64, 386, arm64)
3. **mihomo-android-all** - Package containing binaries for all Android architectures (arm64-v8a, armeabi-v7a, x86, x86_64)

## How It Works

1. **Daily Release Check**  
   - Our GitHub Actions workflow runs every day at **12:10 UTC**
   - It queries the [MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo) repository for the **latest release tag**

2. **Automatic Build & Release**  
   - When a new tag is found, the workflow:
     - Checks out the Mihomo source code with the specific tag
     - Compiles binaries for all supported platforms
     - Creates universal builds by combining architecture-specific binaries
     - Calculates checksums for verification
     - Creates a GitHub Release with all binaries attached

3. **Manual Trigger**  
   - You can manually trigger the workflow via GitHub Actions
   - Simply provide the desired version tag (e.g., `v1.19.3`) in the inputs
   - Optionally, you can choose to delete an existing release with the same tag

## Using the Binaries

### For macOS
Download the `mihomo-darwin-universal-[version].zip` file from the latest release. This single binary works on both Intel (x86_64) and Apple Silicon (arm64) Macs.

```bash
# Extract the zip file
unzip mihomo-darwin-universal-v1.19.3.zip

# Make the binary executable
chmod +x mihomo-darwin-universal

# Run the binary
./mihomo-darwin-universal
```

### For Windows
Download the `mihomo-windows-all-[version].zip` file from the latest release. It contains binaries for all Windows architectures:

- `mihomo-amd64.exe` - For 64-bit Intel/AMD processors (most common)
- `mihomo-386.exe` - For 32-bit Intel/AMD processors (older systems)
- `mihomo-arm64.exe` - For ARM64 processors (newer Windows on ARM devices)

Choose the appropriate version for your system.

### For Android
Download the `mihomo-android-all-[version].zip` file from the latest release. This package follows the standard Android ABI layout:

- `lib/arm64-v8a/mihomo` - For 64-bit ARM devices (most modern phones/tablets)
- `lib/armeabi-v7a/mihomo` - For 32-bit ARM devices (older phones/tablets)
- `lib/x86/mihomo` - For 32-bit x86 Android devices (rare)
- `lib/x86_64/mihomo` - For 64-bit x86 Android devices (some tablets, Chrome OS)

You can integrate these binaries into your Android application or use them with custom solutions.

## Build Details

All binaries are built directly from the official Mihomo source code without modifications. The build process uses Go's cross-compilation capabilities to produce binaries for each target platform and architecture.

For verification purposes, SHA256 checksums for all artifacts are published in each release's description.

Special features of our builds:

- **macOS Universal Binary**: Created using `lipo` to combine arm64 and amd64 builds into a single binary
- **Multi-architecture Packages**: Organized in a user-friendly way with clear documentation
- **Consistent Versioning**: Each build is tagged with the same version as the original Mihomo release

## License

This project adheres to the same license as Mihomo. For more details, please refer to the [Mihomo repository](https://github.com/MetaCubeX/mihomo).
