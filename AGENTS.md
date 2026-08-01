# Repository working conventions

- All commands that can create or modify files in this repository must run as
  the `dave` user. When an escalated shell is required, invoke the mutating
  command through `runuser -u dave -- ...`.
- Never run Bundler, Jekyll, Perl generators, formatters, or dependency
  installers as `root` in this repository.
- Before handing work back, verify that every path under the repository is
  owned by `dave:dave` and repair any mismatch.
