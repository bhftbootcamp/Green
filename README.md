# Orange

[![Registry](https://img.shields.io/badge/registry-Orange-orange)](https://github.com/bhftbootcamp/Orange)

Local registries for the #bhftbootcamp community.

> [!NOTE]  
> These registers are used to organize work with packages that are developed and used within the [#bhftbootcamp](https://github.com/bhftbootcamp) community.
> At the moment, there is no provision for adding third-party custom packages.

## Installation

There are several ways to set registers. The simplest way is to use an https request in REPL mode:

```julia
julia> Pkg.Registry.add(RegistrySpec(url = "https://github.com/bhftbootcamp/Orange.git"))
    Cloning registry from "https://github.com/bhftbootcamp/Orange.git"
      Added registry `Orange` to `~/.julia/registries/Orange`
```

Or simply use the Julia package manager (for more information, see [guide](https://pkgdocs.julialang.org/v1/getting-started/#Basic-Usage)):

```julia
pkg> registry add https://github.com/bhftbootcamp/Orange.git
    Cloning registry from "https://github.com/bhftbootcamp/Orange.git"
      Added registry `Orange` to `~/.julia/registries/Orange`
```

Now packages from [#bhftbootcamp](https://github.com/bhftbootcamp) can be installed as easily as any other packages from [General](https://github.com/JuliaRegistries/General).

### Example

For example, let's install the [NumExpr](https://github.com/bhftbootcamp/NumExpr.jl) package:
```julia
julia> add NumExpr
    Status `~/.julia/environments/v1.10/Project.toml`
      [005f7402] NumExpr v1.0.0
```

If in your environment there are several registers containing packages with identical names, then you will have to select the one you need as follows:
- Select the desired package interactively using the keyboard arrows (REPL mode):
```julia
pkg> add Doppelganger
There are multiple registered `Doppelganger` packages, choose one:
   Registry: General - Repo: https://github.com/AnotherRepo/Doppelganger.jl.git - UUID: ada51f47-0e8a-4e94-b9b4-d01a47782803
 > Registry: Orange - Repo: https://github.com/bhftbootcamp/Doppelganger.jl.git - UUID: d0ee2183-bfee-4e2e-aa29-8fe0fc006c23
```

- Specify the required `uuid` of the package:
```julia
julia> using Pkg
julia> Pkg.add(name = "NumExpr", uuid = "005f7402-6e25-4d9a-960d-a0ddd50a2fba")
    Status `~/.julia/environments/v1.10/Project.toml`
      [005f7402] NumExpr v1.0.0
```
or use the Julia package manager:
```julia
dev> add NumExpr=005f7402-6e25-4d9a-960d-a0ddd50a2fba
    Status `~/.julia/environments/v1.10/Project.toml`
      [005f7402] NumExpr v1.0.0
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
It will force Julia to use your system git instead of default `libgit2` (Require Julia v1.7).
See this [thread](https://discourse.julialang.org/t/julia-repl-is-ignoring-my-ssh-config-file/65287/6) for more information.
