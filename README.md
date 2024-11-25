<div id="vscodium-logo" align="center">
    <br />
    <img src="./icons/stable/codium_cnl.svg" alt="VSCodium Logo" width="200"/>
    <h1><a href="https://vscodium.dev">VSCodium.dev</a></h1>
    <h3>Free/Libre Open Source Software Binaries of [vscode.dev](https://vscode.dev)</h3>
</div>

<div id="badges" align="center">

[![current release](https://img.shields.io/github/release/vscodium/vscodium.svg)](https://github.com/vscodium/vscodium/releases)
[![license](https://img.shields.io/github/license/VSCodium/vscodium.svg)](https://github.com/VSCodium/vscodium/blob/master/LICENSE)
[![Gitter](https://img.shields.io/gitter/room/vscodium/vscodium.svg)](https://gitter.im/VSCodium/Lobby)
[![codium](https://snapcraft.io//codium/badge.svg)](https://snapcraft.io/codium)
[![codium](https://snapcraft.io//codium/trending.svg?name=0)](https://snapcraft.io/codium)

[![build status (linux)](https://img.shields.io/github/actions/workflow/status/MoritzTim/vscodium.dev/stable-linux.yml?branch=master&label=build%28linux%29)](https://github.com/MoritzTim/vscodium.dev/actions/workflows/stable-linux.yml?query=branch%3Amaster)

</div>

**This is a fork of a repository of scripts to automatically build [Microsoft's `vscode` repository](https://github.com/microsoft/vscode) into freely-licensed binaries with a community-driven default configuration, which is not a fork.**

## Table of Contents

- [Download/Install](#download-install)
- [Build](#build)
- [Why Does This Exist](#why)
- [More Info](#more-info)
- [Supported Platforms](#supported-platforms)

## <a id="download-install"></a>Download/Install

:tada: :tada:
Download latest release [here](https://github.com/MoritzTim/vscodium.dev/releases) or see it in action [here](https://vscodium.dev)
:tada: :tada:

[More info / helpful tips are here.](https://github.com/MoritzTim/vscodium.dev/blob/master/docs/index.md)


## <a id="build"></a>Build

Build instructions can be found [here](https://github.com/MoritzTim/vscodium.dev/blob/master/docs/howto-build.md)

## <a id="why"></a>Why Does This Exist

This repository contains build files to generate free release binaries of Microsoft's VS Code for the web and deploy them on [vscodium.dev](https://vscodium.dev). When we speak of "free software", we're talking about freedom, not price.

Microsoft's releases of Visual Studio Code are licensed under [this not-FLOSS license](https://code.visualstudio.com/license) and contain telemetry/tracking. According to [this comment](https://github.com/Microsoft/vscode/issues/60#issuecomment-161792005) from a Visual Studio Code maintainer:

> When we [Microsoft] build Visual Studio Code, we do exactly this. We clone the vscode repository, we lay down a customized product.json that has Microsoft specific functionality (telemetry, gallery, logo, etc.), and then produce a build that we release under our license.
>
> When you clone and build from the vscode repo, none of these endpoints are configured in the default product.json. Therefore, you generate a "clean" build, without the Microsoft customizations, which is by default licensed under the MIT license

This repo exists so that you don't have to download+build+host from source. The build scripts in this repo clone Microsoft's vscode repo, run the build commands, upload the resulting binaries to [GitHub releases](https://github.com/MoritzTim/vscodium.dev/releases) and hosting them on [vscodium.dev](https://vscodium.dev). __These binaries and the website are licensed under the MIT license. Telemetry is disabled.__

If you want to build from source yourself, head over to [Microsoft's vscode repo](https://github.com/Microsoft/vscode) and follow their [instructions](https://github.com/Microsoft/vscode/wiki/How-to-Contribute#build-and-run). This repo exists to make it easier to get the latest version of MIT-licensed VS Code.

Microsoft's build process (which we are running to build the binaries) does download additional files. Those packages downloaded during build are:

- Pre-built extensions from the GitHub:
  - [ms-vscode.js-debug-companion](https://github.com/microsoft/vscode-js-debug-companion)
  - [ms-vscode.js-debug](https://github.com/microsoft/vscode-js-debug)
  - [ms-vscode.vscode-js-profile-table](https://github.com/microsoft/vscode-js-profile-visualizer)
- From [Electron releases](https://github.com/electron/electron/releases) (using [gulp-atom-electron](https://github.com/joaomoreno/gulp-atom-electron))
  - electron
  - ffmpeg

## <a id="more-info"></a>More Info

### Documentation

For more information on getting all the telemetry disabled, tips for migrating from Visual Studio Code to VSCodium and more, have a look at [the Docs page](https://github.com/MoritzTim/vscodium.dev/blob/master/docs/index.md) page.

### Troubleshooting

If you have any issue, please check [the Troubleshooting page](https://github.com/MoritzTim/vscodium/blob/master/docs/troubleshooting.md) or the existing issues.

### Extensions and the Marketplace

According to the VS Code Marketplace [Terms of Use](https://aka.ms/vsmarketplace-ToU), _you may only install and use Marketplace Offerings with Visual Studio Products and Services._ For this reason, VSCodium uses [open-vsx.org](https://open-vsx.org/), an open source registry for VS Code extensions. See the [Extensions + Marketplace](https://github.com/MoritzTim/vscodium.dev/blob/master/docs/index.md#extensions-marketplace) section on the Docs page for more details.

Please note that some Visual Studio Code extensions have licenses that restrict their use to the official Visual Studio Code builds and therefore do not work with VSCodium. See [this note](https://github.com/MoritzTim/vscodium.dev/blob/master/docs/index.md#proprietary-debugging-tools) on the Docs page for what's been found so far and possible workarounds.

### How are the VSCodium binaries built?

If you would like to see the commands we run to build `vscode` into VSCodium binaries, have a look at the workflow files in `.github/workflows` for Windows, GNU/Linux and macOS. These build files call all the other scripts in the repo. If you find something that doesn't make sense, feel free to ask about it [on Gitter](https://gitter.im/VSCodium/Lobby).

The builds are run every day, but exit early if there isn't a new release from Microsoft.

## <a id="supported-platforms"></a>Supported Platforms

The following platforms can be used to host the web builds:

- [x] macOS (`zip`, `dmg`) macOS 10.15 or newer x64
- [x] macOS (`zip`, `dmg`) macOS 11.0 or newer arm64
- [x] GNU/Linux x64 (`deb`, `rpm`, `AppImage`, `snap`, `tar.gz`)
- [x] GNU/Linux arm64 (`deb`, `rpm`, `snap`, `tar.gz`)
- [x] GNU/Linux armhf (`deb`, `rpm`, `tar.gz`)
- [x] GNU/Linux loong64 (`tar.gz`)
- [x] Windows 10 / Server 2012 R2 or newer x64

## <a id="thanks"></a>Special thanks

<table>
  <tr>
    <td><a href="https://github.com/jaredreich" target="_blank">@jaredreich</a></td>
    <td>for the logo</td>
  </tr>
  <tr>
    <td><a href="https://github.com/PalinuroSec" target="_blank">@PalinuroSec</a></td>
    <td>for CDN and domain name</td>
  </tr>
  <tr>
    <td><a href="https://www.macstadium.com" target="_blank"><img src="https://images.prismic.io/macstadium/66fbce64-707e-41f3-b547-241908884716_MacStadium_Logo.png?w=128&q=75" width="128" height="49" alt="MacStadium logo" /></a></td>
    <td>for providing a Mac mini M1</td>
  </tr>
  <tr>
    <td><a href="https://github.com/daiyam" target="_blank">@daiyam</a></td>
    <td>for macOS certificate</td>
  </tr>
  <tr>
    <td><a href="https://signpath.org/" target="_blank"><img src="https://avatars.githubusercontent.com/u/34448643" height="30" alt="SignPath logo" /></a></td>
    <td>free code signing on Windows provided by <a href="https://signpath.io/" target="_blank">SignPath.io</a>, certificate by <a href="https://signpath.org/" target="_blank">SignPath Foundation</a></td>
  </tr>
  <tr>
    <td><a href="https://github.com/GitMensch" target="_blank">@GitMensch</a></td>
    <td>for authorizing this project</td>
  </tr>
</table>

## <a id="license"></a>License

[MIT](https://github.com/MoritzTim/vscodium.dev/blob/master/LICENSE)
