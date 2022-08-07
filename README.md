---

title: README
description: Zig development tools for Neovim
authors: NTBBloodbath
categories: zig dev-tools neovim
created: 2022-08-06
version: 0.0.11
---


# zig-tools.nvim

zig-tools.nvim is a Neovim (>= 0.7.x) plugin that adds some Zig-specific features to Neovim. WIP.

zig-tools.nvim aims to provide Zig integration to your favorite editor, and that integration is a
swiss army knife, all-in-one. That means, zig-tools.nvim will provide an integration with Zig
build system (by using your project `build.zig`), available third-party dependencies managers
(zigmod and gyro) and ZLS (Zig Language Server).

For example, zig-tools.nvim will create commands to run specific `build.zig` tasks, compile
_and run_ your project, live _automatic_ rebuild, add/remove/update dependencies, etc.


## Design mantra

- **Freedom**. You are free to use _and do_ only what you want and only when you want.
  zig-tools.nvim will never force you to use one of its features.
- **Simplicity**. Development tools should be mnemonic, easy to understand _and use_.
- **Your setup, your choices**. Nobody better than you knows what is best for your system and your
  Neovim setup, zig-tools.nvim will take care not to get in your way.


## Features

- Zig build system integration.
    - Compile _and run_ your project.
    - Live rebuild on changes.
    - Run your additional build tasks (e.g. `zig build tests`).
- opt-in Zig third-party dependencies managers integration (add, remove and update your
  zigmod/gyro dependencies on the fly!).
- opt-in LSP integration (with support for inlay hints, thanks to rust-tools.nvim author). See
  [FAQ](#faq) if you have questions about this integration.


## Requirements

- Neovim (>= 0.7.x)
- ripgrep (>= 11.0)


## Installation

You can use your favorite plugins manager to get zig-tools.nvim, we are going to use packer here:
```lua
use({
  "NTBBloodbath/zig-tools.nvim",
  -- Load zig-tools.nvim only in Zig buffers
  ft = "zig",
  config = function()
    -- Initialize with default config
    require("zig-tools").setup()
  end,
  requires = { "akinsho/toggleterm.nvim" }
})
```


## FAQ

> Last design mantra says that zig-tools.nvim is not going to get in my way but it can also
> manage zls installation. How does it make sense?

zig-tools.nvim `zls` management works pretty differently from Neovim plugins like lsp-installer.
That means, zig-tools.nvim will only download `zls` from your chosen installation method (gh
releases or build from source) and then move `zls` binary to your `PATH` so you can set up `zls`
yourself by using `nvim-lspconfig` with no weird abstractions.


## License

As all my other projects, zig-tools.nvim is licensed under [GPLv3](./LICENSE) license.