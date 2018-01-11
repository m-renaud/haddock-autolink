# Haddock Autolink

A [Sphinx](www.sphinx-doc.org) extension for automatically linking to Haddocks
for Haskell packages.

## How to use the autolinker

This extension provides two autolinkers: `:haddock:` and `:haddock_short:` which
take a string of the form `package-name/Module.Name#identifier` and generate a
link to the Haddocks. `:haddock:` will have the module name and identifier in
the link text, `:haddock_short:` will only have the identifier.

You can omit the identifier to link directly to the module
(`containers/Data.Sequence`), and you can omit the module and identifier to link
to the package (`containers`).


### Implicit Haddock Links

If you are writing documentation for the `foo` haskell package (`project =
'foo'` in your ReadTheDoc's `conf.py`) then you can omit the `package-name` part
of the `package-name/Module.Name#identifier` and instead just put
`/Module.Name#identifier`.


### Examples

```
:haddock:`containers`
```
=> [containers](https://hackage.haskell.org/package/containers)

```
:haddock:`containers/Data.Sequence`
```
=> [Data.Sequence](https://hackage.haskell.org/package/containers/docs/Data-Sequence.html)

```
:haddock:`containers/Data.Sequence#empty`
```
=> [Data.Sequence#empty](https://hackage.haskell.org/package/containers/docs/Data-Sequence.html#v:empty)


## Installing the extension

If you are using the [Haskell Package ReadTheDocs template]() all you need to do is
initialize the already set-up submodule in the `_extensions` directory.

If you are not using the template, we recommend you install this as a submodule
so you get any updates to the extension.


## Other Haddock Hosting Options

This autolinker supports linking to non-Hackage documentation, currently
Stackage and local docs are supported.

### Linking to Stackage

To link to Stackage you'll need to set two environment variables when building
the documentation:

- `HADDOCK_HOST=stackage`
- `STACKAGE_RESOLVER=<resolver>` where `<resolver>` is the Stackage resolver you
  want to link to (for example, `lts-10.0`)


### Linking to local docs

You can also link to locally hosted Haddocks by setting:

- `HADDOCK_HOST=local`
- `HADDOCK_DIR=<path-to-haddock-root>` (for example `file:///path/to/haddocks/`)
