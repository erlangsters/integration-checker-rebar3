# Integration with Rebar3 checker

The sole purpose of this repository is to check if all Erlangsters projects
integrates well with the Rebar3 build system.

All projects it's checking.

- Erlang Term Validator

Instead of a thorough check for all platforms, all architectures and all
Erlang versions, it only checks using the latest stable 'erlang' image on Linux
as we assume that backward compatibility is maintained and we're mostly
interested in detecting issues early with the latest version of Erlang/OTP and
Rebar3 build system.

## Checking a project

Download the latest version of the Rebar3 build system.

```
wget https://s3.amazonaws.com/rebar3/rebar3
chmod +x rebar3
```

To check if a project integrates well, create a rebar.config of the
rebar.config.in by replacing the `@project_name` and `@project_repo` with the
values of the project you want to check.

```sh
sed \
    -e 's/@project_name/etv/g' \
    -e 's/@project_repo/erlang-term-validator/g' \
    rebar.config.in > rebar.config
```

Then run the compile command.

```sh
rebar3 compile
```

If it completes successfully, the project integrates well.
