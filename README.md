ConfuserEx
========
ConfuserEx is a open-source protector for .NET applications.
It is the successor of [Confuser](http://confuser.codeplex.com) project.

## About this LTRData fork

This repository retains the original [yck1509/ConfuserEx](https://github.com/yck1509/ConfuserEx) source and a separate branch with LTRData changes built on [mkaring/ConfuserEx](https://github.com/mkaring/ConfuserEx).

**The discontinuation notice below describes the original yck1509 project. LTRData's later work is on `LTRData.ConfuserEx-initial`, not the default `master` branch.**

| Branch | Contents |
| --- | --- |
| [`master`](https://github.com/LTRData/ConfuserEx/tree/master) (default) | Original upstream snapshot, including the January 2019 README notice. |
| [`LTRData.ConfuserEx-initial`](https://github.com/LTRData/ConfuserEx/tree/LTRData.ConfuserEx-initial) | LTRData customizations plus changes from the mkaring fork; last updated in October 2021. |
| [`gh-pages`](https://github.com/LTRData/ConfuserEx/tree/gh-pages) | Historical website content. |

These are historical snapshots. The existence of the later branch does not imply ongoing maintenance or synchronization with either upstream project.

### LTRData changes

The [differences from the last merged mkaring revision](https://github.com/LTRData/ConfuserEx/compare/82c9c12ff6f70885e62f3a8a38d88da6969ba8e5...9dbe78528499c4d099fd9208d685d6420e279918) include:

- Additional renaming exclusions for serializable types and their members, and for data-contract types and properties.
- A startup hook in the compressed executable runtime for a companion `<executable-name>.Splash.dll`.
- Replacement of managed SHA implementations in core helpers with Windows cryptographic service provider implementations.
- CLI configuration/manifest changes and build updates, including C# 9 language settings.

The broader changes inherited from mkaring are separate from these LTRData customizations.

### Building and using the source

To check out the LTRData branch explicitly:

```sh
git clone --branch LTRData.ConfuserEx-initial https://github.com/LTRData/ConfuserEx.git
cd ConfuserEx
```

On that branch, `Confuser2.sln` contains the CLI, WPF GUI, core/protection/renaming libraries, MSBuild integration and tests. The CLI and GUI target .NET Framework 4.6.1; the core, protection, renaming and MSBuild projects target .NET Framework 4.6.1 and .NET Standard 2.0. The injected runtime project targets .NET Framework 2.0. These build targets do not by themselves establish compatibility with every application being processed.

The branch uses SDK-style projects, NuGet dependencies (including dnlib 3.3.4) and a C# 9-capable compiler. Building the GUI requires Windows/WPF tooling, and .NET Framework targets require their reference assemblies. Inspect the selected projects for additional requirements, particularly the native test projects.

The default `master` branch instead uses legacy project files and a dnlib Git submodule. When working on that historical branch, initialize it with `git submodule update --init --recursive`; do not apply the later branch's build requirements to it.

The CLI accepts a `*.crproj` project file. See the [project format on the LTRData branch](https://github.com/LTRData/ConfuserEx/blob/LTRData.ConfuserEx-initial/docs/ProjectFormat.md) for configuration. Licensing is recorded in [LICENSE](LICENSE) on `master` and [LICENSE.md](https://github.com/LTRData/ConfuserEx/blob/LTRData.ConfuserEx-initial/LICENSE.md) on the later branch.

## Inherited original README

The notice, framework list, feature plans and reporting links below belong to the original project. They are retained as historical context rather than a maintenance or support statement for the LTRData branch.

---

NOTICE
======
This project is discontinued and unmaintained. Alternative forked projects can be found in [this issue](https://github.com/yck1509/ConfuserEx/issues/671).

Features
--------
* Supports .NET Framework 2.0/3.0/3.5/4.0/4.5
* Symbol renaming (Support WPF/BAML)
* Protection against debuggers/profilers
* Protection against memory dumping
* Protection against tampering (method encryption)
* Control flow obfuscation
* Constant/resources encryption
* Reference hiding proxies
* Disable decompilers
* Embedding dependency
* Compressing output
* Extensible plugin API
* Many more are coming!

Usage
-----
`Confuser.CLI <path to project file>`

The project file is a ConfuserEx Project (*.crproj).
The format of project file can be found in docs\ProjectFormat.md

Bug Report
----------
See the [Issues Report](http://yck1509.github.io/ConfuserEx/issues/) section of website.


License
-------
See LICENSE file for details.

Credits
-------
**[0xd4d](https://github.com/0xd4d)** for his awesome work and extensive knowledge!  
Members of **[Black Storm Forum](http://board.b-at-s.info/)** for their help!
