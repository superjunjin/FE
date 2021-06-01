# Deno

A **secure** runtime for **JavaScript** and **TypeScript**.

\(Deno为**JavaScript**和**TypeScript**提供安全的运行时环境\)

Deno is a simple, modern and secure runtime for JavaScript and TypeScript that uses V8 and is built in Rust.

\(Deno为**JavaScript**和**TypeScript**提供简单的，现代的和安全的运行时环境，它是使用V8引擎的并且用Rust语言开发而成\)

* Secure by default. No file, network, or environment access, unless explicitly enabled.

  （默认安全的，除非显式使用，否则不能访问文件，网络，环境等）

* Supports TypeScript out of the box.

  （支持TypeScript的开箱即用）

* Ships only a single executable file.

  （只发布一个可执行文件。）

* Has built-in utilities like a dependency inspector \(`deno info`\) and a code formatter \(`deno fmt`\).

  （具有内置的工具，如依赖检查器和代码格式化器）

* Has a set of reviewed \(audited\) standard modules that are guaranteed to work with Deno: [deno.land/std](https://deno.land/std)

  （有一组经过审查的标准模块可以保证与Deno一起工作）

## [Installation](https://deno.land/#installation)

Deno ships as a single executable with no dependencies. You can install it using the installers below, or download a release binary from the [releases page](https://github.com/denoland/deno/releases).

（Deno作为一个单独的可执行文件发布，没有依赖关系。您可以使用下面的安装程序安装它，或者从发布页面下载发布二进制文件。）

Shell \(Mac, Linux\):

```text
curl -fsSL https://deno.land/x/install/install.sh | sh
```

PowerShell \(Windows\):

```text
iwr https://deno.land/x/install/install.ps1 -useb | iex
```

[Homebrew](https://formulae.brew.sh/formula/deno) \(Mac\):

```text
brew install deno
```

[Chocolatey](https://chocolatey.org/packages/deno) \(Windows\):

```text
choco install deno
```

[Scoop](https://scoop.sh/) \(Windows\):

```text
scoop install deno
```

Build and install from source using [Cargo](https://crates.io/crates/deno):

```text
cargo install deno --locked
```

See [deno\_install](https://github.com/denoland/deno_install) for more installation options.

## [Getting Started](https://deno.land/#getting-started)

Try running a simple program:

```text
deno run https://deno.land/std/examples/welcome.ts
```

Or a more complex one:

```javascript
import { serve } from "https://deno.land/std@0.90.0/http/server.ts";
const s = serve({ port: 8000 });
console.log("http://localhost:8000/");
for await (const req of s) {
  req.respond({ body: "Hello World\n" });
}
```

You can find a more in depth introduction, examples, and environment setup guides in [the manual](https://deno.land/manual).

\(您可以在手册中找到更深入的介绍、示例和环境设置指南。\)

## [Runtime Documentation](https://deno.land/#runtime-documentation)

The basic runtime documentation for Deno can be found on [doc.deno.land](https://doc.deno.land/builtin/stable).

Deno comes with [a manual](https://deno.land/manual) which contains more in depth explanations about the more complex functions of the runtime, an introduction to the concepts that Deno is built on, details about the internals of Deno, how to embed Deno in your own application and how to extend Deno using Rust plugins.

（Deno随附一本手册，其中包含有关运行时更复杂功能的更深入说明，对Deno构建的概念的介绍，有关Deno内部的详细信息，如何将Deno嵌入您自己的应用程序以及如何扩展 Deno使用Rust插件。）

The manual also contains information about the built in tools that Deno provides.

（该手册还包含有关Deno提供的内置工具的信息。）

## [Standard Modules](https://deno.land/#standard-modules)

Next to the Deno runtime, Deno also provides a list of audited standard modules that are reviewed by the Deno maintainers and are guaranteed to work with a specific Deno version. These live alongside the Deno source code in the [denoland/deno](https://github.com/denoland/deno) repository.

（除了Deno运行时，Deno还提供了一系列经过审核的标准模块，这些模块已由Deno维护人员进行了审查，并保证可以与特定的Deno版本一起使用。 这些与Deno / deno存储库中的Deno源代码一起存在）

These standard modules are hosted at [deno.land/std](https://deno.land/std) and are distributed via URLs like all other ES modules that are compatible with Deno.

（这些标准模块托管在deno.land/std中，并且像与Deno兼容的所有其他ES模块一样，通过URL进行分发。）

## [Third Party Modules](https://deno.land/#third-party-modules)

Deno can import modules from any location on the web, like GitHub, a personal webserver, or a CDN like [Skypack](https://www.skypack.dev/), [jspm.io](https://jspm.io/), [jsDelivr](https://www.jsdelivr.com/) or [esm.sh](https://esm.sh/).

（Deno可以从web上的任何位置导入模块，比如GitHub，个人网络服务器，或者像Skypack, jspm这样的CDN。. io、jsdelivery或esm.sh。）

To make it easier to consume third party modules Deno provides some built in tooling like `deno info` and `deno doc`. deno.land also provides a web UI for viewing module documentation. It is available at [doc.deno.land](https://doc.deno.land/).

（为了更轻松地使用第三方模块，Deno提供了一些内置工具，例如deno info和deno doc。 deno.land还提供了一个Web UI，用于查看模块文档。 可从doc.deno.land获得。）

deno.land also provides a simple public hosting service for ES modules that work with Deno. It can be found at [deno.land/x](https://deno.land/x).

（deno.land还为与Deno合作的ES模块提供了简单的公共托管服务。 可以在deno.land/x中找到。）

