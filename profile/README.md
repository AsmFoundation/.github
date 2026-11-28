<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/seal-print-dark.svg">
  <img width="560" alt="The AsmFoundation seal: the 1,854 letters of the x86-64 one-byte opcode table, as a ring reading FREE OPEN SOURCE ASSEMBLY SOFTWARE around the AsmFoundation A." src="./assets/seal-print-light.svg">
</picture>

### Free Open Source Assembly Software

Competitive cloud/backend infrastructure, written in assembly, with exceptional performance for any
platform or container.<br>
The AsmSdk toolchain allows integration with most of the modern programming languages through pinvoking that
AsmSdk manages and exports<br>
Allowing transparent integration into most programming languages.

**[asmfoundation.github.io](https://asmfoundation.github.io/)**

[Projects](https://asmfoundation.github.io/projects/) &nbsp;&nbsp; [Benchmarks](https://asmfoundation.github.io/benchmarks/) &nbsp;&nbsp; [Architecture](https://asmfoundation.github.io/architecture/) &nbsp;&nbsp; [Get started](https://asmfoundation.github.io/get-started/) &nbsp;&nbsp; [Docs](https://asmfoundation.github.io/docs/)

</div>

---

<!--
  The drawing below is the website's Architecture page. The site build in AsmFoundation/AsmFoundation writes it
  from site/data/architecture.json to https://asmfoundation.github.io/architecture/drawing.svg, and this page
  shows that file. Change the drawing there, never here: it updates on this page after the next build.
-->
<a href="https://asmfoundation.github.io/architecture/"><img alt="The foundation's architecture, drawn as a building: the services on top, standing on the protocols, the build and the machine code, each marked released, in development, in design or not started." src="https://asmfoundation.github.io/architecture/drawing.svg"></a>

| Project | What it is | State |
|---|---|---|
| **[AsmSdk](https://github.com/AsmFoundation/AsmSdk)** | SDK toolchain that builds native binaries from assembly with `dotnet build` for Windows, Linux and macOS on x64 and ARM64, and WebAssembly. | **0.4.0** |
| **[HttpAsm](https://github.com/AsmFoundation/HttpAsm)** | A complete HTTP networking library in cross-platform assembly: HTTP/1.1, HTTP/2 and HTTP/3 with QUIC and TLS | in&nbsp;development (M1&nbsp;done) |
| **[GrpcAsm](https://github.com/AsmFoundation/GrpcAsm)** | A gRPC server and client in assembly, with NASM, C and .NET APIs | in&nbsp;development |
| **StorageAsm** | Object storage over gRPC | in design |
| **ContainersAsm** | A container runtime and shim in assembly, and LinuxAsmOS images | in&nbsp;development |
| **[KvAsm](https://github.com/AsmFoundation/KvAsm)** | A gRPC key-value server | **0.3.0** |
| **[AsmClaudeMarketplace](https://github.com/AsmFoundation/AsmClaudeMarketplace)** | Claude Code plugins for this ecosystem | asmsdk **0.4.0** |

The measurements, one core first, are on the [Benchmarks](https://asmfoundation.github.io/benchmarks/)
page, each with the run behind it.

### Language compatibility

| Language | How it works with the foundation | Examples |
|---|---|---|
| **Assembly** | Every project is written in it: NASM for x64, GNU syntax for ARM64, LLVM's for WebAssembly, built with `dotnet build` as `.asmproj` projects that reference each other and ship as NuGet packages | [AsmSdk's samples](https://github.com/AsmFoundation/AsmSdk/tree/main/samples), [GrpcAsm's Greeter](https://github.com/AsmFoundation/GrpcAsm/tree/main/samples/Greeter), [HttpAsm's Hello](https://github.com/AsmFoundation/HttpAsm/tree/main/samples/Hello) |
| **.NET** (C#), first&nbsp;class | A `ProjectReference` or `PackageReference` to an .asmproj (asm project) brings each platform's binary and the C# bindings the SDK writes from its `PROTO` lines. GrpcAsm runs your grpc-dotnet service classes, and KvAsm has a NuGet client | [Crc32C](https://asmfoundation.github.io/AsmSdk/examples/crc32c.html), [GreeterNet](https://github.com/AsmFoundation/GrpcAsm/tree/main/samples/GreeterNet), [KvAsm.Client](https://github.com/AsmFoundation/KvAsm/tree/main/client/dotnet) |
| **C and C++** | Plain C ABI libraries, shared or static, with a header the SDK writes (`<name>.h`); GrpcAsm and HttpAsm have C APIs | [GreeterC](https://github.com/AsmFoundation/GrpcAsm/tree/main/samples/GreeterC), [Crc32C from C++](https://asmfoundation.github.io/AsmSdk/examples/callers.html#c) |
| **Python** | `ctypes`, or `cffi` reading the same header; GrpcAsm's Python API is next | [a package around Crc32C](https://asmfoundation.github.io/AsmSdk/examples/callers.html#python-a-package-with-the-library-in-its-wheel), [a KvAsm client](https://github.com/AsmFoundation/KvAsm/tree/main/examples/python) |
| **Rust, Go, Zig** | Their C FFI (`extern "C"`, cgo, Zig's translate-c) over the same libraries | Crc32C from [Rust](https://asmfoundation.github.io/AsmSdk/examples/callers.html#rust), [Go](https://asmfoundation.github.io/AsmSdk/examples/callers.html#go) and [Zig](https://asmfoundation.github.io/AsmSdk/examples/callers.html#zig) |
| **JavaScript** | WebAssembly modules, in browsers, Node, Deno and Bun | [the Wasm Demos](https://asmfoundation.github.io/AsmSdk/demos/), [a module from Node](https://github.com/AsmFoundation/AsmSdk/tree/main/src/AsmFoundation.Templates/templates/asmwasm) |
| **Any gRPC language** | KvAsm and GrpcAsm speak standard gRPC, so Java, Go, Python, Node and Rust clients work as they are | [KvAsm from Python and Go](https://github.com/AsmFoundation/KvAsm/tree/main/examples) |

### Try it

```sh
docker run --rm -p 50051:50051 ghcr.io/asmfoundation/kvasm:0.3.0
```

```json
{ "msbuild-sdks": { "AsmFoundation.Sdk": "0.4.0" } }
```

```sh
dotnet new install AsmFoundation.Templates
dotnet new asmnet -n Demo          # a C# app, the assembly library it calls, and its tests
```

The whole session, step by step: [Get started](https://asmfoundation.github.io/get-started/).

### Get involved

Issues and pull requests are welcome in every repository:
[CONTRIBUTING.md](https://github.com/AsmFoundation/.github/blob/main/CONTRIBUTING.md) says what a change
needs, and a performance change needs a paired measurement. Report vulnerabilities privately
([SECURITY.md](https://github.com/AsmFoundation/.github/blob/main/SECURITY.md)). Every project is
Apache-2.0.
