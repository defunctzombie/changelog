# changelog

A tool for updating project changelogs and package.json files for new releases.

## Why?

Having a changelog (or history) file in a project helps you communicate to your users (developers) which changes you find most important to a release. Obviously the commit history is always available, but is often filled with noise. The changelog is a noise free place to highlight thee major changes in a more summarized and human readable form.

Currently workflows do not put enough emphasis on the changelog. Developers will often make a series of commits and then just bump the version in package.json. By centering the versioning workflow around the changelog, I hope to encourage more modules to keep an updated history.

## Workflow

### install the changelog tool

```shell
npm install -g defunctzombie/changelog
```

### create an empty initial changelog

```shell
changelog --init
```

A `HISTORY.md` file will be created with the following content

```md
# UNRELEASED

  * initial
```

### release a new version

After you make some commits and add entries to the changelog, you can release a new version using the `--release` flag

```shell
changelog --release 1.0.0
```

This will perform the following:
* Update the first changelog `UNRELEASED` line to `# 1.0.0 (YYYY-MM-DD)`.
* Set the version in `package.json`
* `git commit v<new version>`
* `git tag v<new version>`

### bump to UNRELEASED

This will add a new `UNRELEASED` line to the start of the changelog.

```shell
changelog --increment
```

## changelog format

```md
# UNRELEASED

  * summary item
  * summary item

# 1.0.0 (YYYY-MM-DD)

  * summary item

# 0.1.0 (YYYY-MM-DD)

  * summary item
  * initial
```

The reason `UNRELEASED` is used at the top of the changelog is to indicate a series of changes which have not yet been officially tagged. It may be that a particular change will case a minor or major version bump and so the version cannot be known until a release is ready.

