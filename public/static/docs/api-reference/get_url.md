# dvc.api.get_url()

Returns the full URL to the physical location (in a
[DVC remote](/doc/command-reference/remote)) of a <abbr>data artifact</abbr>
specified by its `path` in a `repo` (<abbr>DVC project</abbr>).

> For possible URL formats, refer to the
> [supported remote types](https://dvc.org/doc/command-reference/remote/add#supported-storage-types)

## Signature

```py
get_url(path, repo=None, rev=None, remote=None)
```

## Parameters

- **`path`** - used to specify the location of the target artifact within the
  source project in `repo`, relative to the project's root.

- `repo` - specifies the location of the source DVC project. Both HTTP and SSH
  protocols are supported for online Git repositories (e.g.
  `[user@]server:project.git`). `repo` can also be a local file system path to
  an "offline" project. If not supplied, this defaults to the current working
  directory.

- `rev` - (optional)
  [Git-revision](https://git-scm.com/book/en/v2/Git-Internals-Git-References)
  (such as a branch name, a tag, or a commit hash). `rev` only has an effect
  when a URL is supplied as parameter to `repo`. If not supplied, it uses the
  default Git revision, `HEAD`.

- `remote` - (optional) name of the [DVC remote](/doc/command-reference/remote)
  to fetch the target artifact from. If not supplied, the default project's
  remote is used.

## Example

```py
import dvc.api

resource_url = dvc.api.get_url("data/data.xml", repo="https://github.com/iterative/example-get-started")

# resource_url = https://remote.dvc.org/get-started/a3/04afb96060aad90176268345e10355
```