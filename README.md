# Green :green_apple:

[![Registry](https://img.shields.io/badge/registry-Green-green)](https://github.com/bhftbootcamp/Green)

Our registry is a tasty addition to the usual General Registry. We serve up a variety of flavorful packages that add some zest to your development experience. Whether you're seeking extra functionality or unique tools, we've got something juicy for everyone!

> [!NOTE]  
> These registers are used to organize work with packages that are developed and used within the [#bhftbootcamp](https://github.com/bhftbootcamp) community.
> At the moment, there is no provision for adding third-party custom packages.

## Installation

You can set registers in your julia environment through the package manager (for more information, see [guide](https://pkgdocs.julialang.org/v1/getting-started/#Basic-Usage)):

```julia-repl
] registry add https://github.com/bhftbootcamp/Green.git
```

Or by running the following code in REPL:
```julia
using Pkg

Pkg.Registry.add(RegistrySpec(; url = "https://github.com/bhftbootcamp/Green.git"))
```

If you’ve followed the steps correctly, the registry should now be successfully added to your environment.

However, if you encounter any issues, please refer to the [troubleshooting](#troubleshooting) section or create an [issue](https://github.com/bhftbootcamp/Green/issues). Doing so may help us streamline the installation process!

## Usage

Once you have installed Green registers in your Julia environment, you can install any package from [#bhftbootcamp](https://github.com/bhftbootcamp) just as easily as any other package from [General](https://github.com/JuliaRegistries/General).

For example, let's install the [NumExpr](https://github.com/bhftbootcamp/NumExpr.jl) package:
```julia
] add NumExpr
```

## Duplicate package names

If you find yourself in an environment with multiple registers containing packages that share identical names, you will be prompted by REPL:
```julia
pkg> add Doppelganger
There are multiple registered `Doppelganger` packages, choose one:
   Registry: General - Repo: https://... - UUID: ada51f47-...
 > Registry: Green - Repo: https://... - UUID: d0ee2183-...
```

Alternatively, you can directly specify the UUID either in package manager:
```julia
] add NumExpr=005f7402-6e25-4d9a-960d-a0ddd50a2fba
```

Or in REPL:
```julia
using Pkg

Pkg.add(; name = "NumExpr", uuid = "005f7402-6e25-4d9a-960d-a0ddd50a2fba")
```

## Troubleshooting

If you are having trouble adding registers to your Julia environment due to `ssh-agent` or other limitations of the standard `libgit2`, you can set the following value to your system environment (MacOS/Linux):
```shell
export JULIA_PKG_USE_CLI_GIT=true
```
or (Windows):
```shell
set JULIA_PKG_USE_CLI_GIT=true
```
It will force Julia to use your system git instead of default `libgit2` (Requires Julia v1.7).
See this [thread](https://discourse.julialang.org/t/julia-repl-is-ignoring-my-ssh-config-file/65287/6) for more information.
