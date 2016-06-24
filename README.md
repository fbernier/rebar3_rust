# rebar3_rust

Compile rust NIFs for erlang projects.

## Use

Add the plugin and hooks to your `rebar.config`

```erlang
{
  plugins,
  [
    {
      rebar3_rust,
      {
        git,
        "https://github.com/sdwolf/rebar3_rust.git",
        {branch, "master"}
      }
    }
  ]
}.

{
  provider_hooks,
  [
    {
      post,
      [
        {compile, {rust, compile}},
      ]
    }
  ]
}.
```

You can find an example usage [here](https://github.com/sdwolf/rust).

## Upgrade

```bash
rebar3 plugins upgrade rebar3_rust
```

## Development

Go inside the downloaded dependency folder:

```bash
cd _build/default/plugins/rebar3_rust
```

Start your erlang docker container:

```bash
docker-here erlang bash

# Or use the full command if you do not have the docker-here alias:
docker run --rm -it -u `id -u`:`id -g` -v "$PWD":/work -w /work erlang bash
```

Compile from a dependent project:

```bash
rebar3 compile && rm -rf ebin/ && mv _build/default/lib/rebar3_rust/ebin/ .
```

## Resources

https://github.com/goertzenator/erlang_nif-sys
