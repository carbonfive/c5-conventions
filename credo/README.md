C5 Elixir Conventions
---------------------

Carbon Five uses [Credo](https://github.com/rrrene/credo) for Elixir static analysis. We have generally chosen to take the [community defaults](https://github.com/rrrene/elixir-style-guide) built into the tool with the following exceptions:

__Default Line Length__: Bumped up to 120 characters

__Lowered priority of [@moduledoc check](https://github.com/rrrene/elixir-style-guide#doc-false)__: Though a good idea to include, not all modules need `@moduledoc` annotations.

__Lowered priority of [raw value pipe chain check](https://github.com/rrrene/elixir-style-guide#pipe-chains)__: Starting all pipe chains with a raw value can sometimes obscure author intent. For example, Ecto queries:

```elixir
(e in Employee, where: e.id in ^to_delete) |> from |> Repo.delete_all
```

look much better when they begin with a function call, as they were designed to be written:

```elixir
from(e in Employee, where: e.id in ^to_delete) |> Repo.delete_all
```

#### Future

Depending on the direction of the Elixir community, this convention doc may be made obsolete with the introduction of tools like [exfmt](https://github.com/lpil/exfmt) which auto-format Elixir code based on a consistent set of rules.
