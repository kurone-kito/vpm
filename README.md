# 🐱 [My VPM Packages](https://kurone-kito.github.io/vpm/)

This registry can be used from both the VRChat Creator Companion (VCC) and
ALCOM.

## Contributing

Welcome to contribute to this repository! For more details,
please refer to [CONTRIBUTING.md](.github/CONTRIBUTING.md).

## Development

This site is generated from `source.json` using Scriban templates.
The repositories listed in `source.json` are processed by the
[package-list-action](https://github.com/vrchat-community/package-list-action)
NUKE scripts and merged with the templates under the `Website` directory.
Some files look unusual because they contain Scriban statements.

Building requires the .NET&nbsp;8 SDK. The version `8.0.403` is pinned in
[`global.json`](global.json), so ensure a matching SDK is installed.

The workflow below reproduces what the CI does:

```bash
git clone https://github.com/kurone-kito/vpm.git
cd vpm
git clone https://github.com/vrchat-community/package-list-action.git ci
"ci/build.cmd" BuildMultiPackageListing --root ci --list-publish-directory Website
```

Serve the generated `Website` directory with any web server to preview locally.
When `source.json` changes, the same build runs on GitHub Actions and the result
is published via GitHub Pages.

The build will move to a *Node.js implementation in the future*.

## License

This repository is licensed under the [MIT License](LICENSE).

However, the license may differ depending on the referenced package.
You should check the license of each repository.
