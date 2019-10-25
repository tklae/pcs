# pcs - project cheat sheet

## tl;dr
pcs is a cheat sheet tool and task runner for the command line that allows running commands 
defined in simple yaml files within a hierarchical project structure.

## Motivation
We've been working a lot in projects with many different git repositories, mono-repositories 
and microservices written in different technologies using different tools.
Remembering all the different commands that can be run in each folder for running tests, 
building or starting the application can become slightly challenging for people who've been 
there a while but for people joining the project, it's usually a real nightmare.

We therefore want to provide an easy way to provide the possible commands to run within 
a directory structure.

## Development setup
We're always happy about people contributing to this project and this section aims to explain
how to do that.

The project currently uses pnpm as the package manager which can be installed via:
```
npm add -g pnpm
```
(Note that npm or yarn should also work for running all of the tasks but the 
`package-lock.json/yarn.lock` files that they generate are currently .gitignore'ed.)

To install all dependencies, simply run 
```
pnpm install
```

Available scripts for building and running the project can be found in the `scripts`-Section
of the [package.json](./package.json).

### Typical development workflow

- `git pull --rebase`
- `pnpm run build` includes linting and running tests to make sure everything you 
checked out is up and running.
- Make your additions/changes to code and tests
- `pnpm run build` to continuously run everything or just `pnpm run test`/`pnpm run lint` 
for tests or linting
- `pnpm run start -- <command>` to test running a command that has to be present in the
[.pcs.yml](./.pcs.yml)
- `pnpm link` to "install" pcs as a command line tool with the current state. Make sure to
reload your terminal/open a new terminal for the changes to be effective.
- `pnpm unlink` to remove the link to the current executable (!Currently does not work, see 
[this bug report](https://github.com/pnpm/pnpm/issues/1584) for details).
