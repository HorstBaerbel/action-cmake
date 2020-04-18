# action-cmake - A GitHub action to build a repository using CMake

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Builds a repository using [CMake](https://cmake.org/).

If you find a bug or make an improvement your pull requests are appreciated.

## License

All of this is under the [MIT License](LICENSE).

## Usage

Create a new workflow file, e.g. ./github/workflows/build.yml:

```yaml
# Build repository using CMake
name: Build

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Build
      uses: HorstBaerbel/action-cmake@1.0
      # These are optional (defaults displayed)
      with:
        sourcedir: '.'
        builddir: 'build'
        cmakeoptions: ''
```

## Parameters (optional), see action.yml

* **sourcedir**: Directory with top-level CMakeLists.txt. MUST be realtive to you repository, thus '.' means root of repository.
* **builddir**: Directory to run CMake build in, e.g. 'build'. MUST be relative to sourcedir, thus 'build' means 'sourcedir/build'.
* **cmakeoptions**: Pass an additional option string to cmake (will call "cmake cmakeoptions sourcedir").
