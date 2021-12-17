# Metachromium
## Metachromium is a new kind of browser for the spatial web
### part of the [Webaverse](https://webaverse.com) initiative

#### Building Metachromium
--------------
**Important: follow this path as written.** You might be tempted to simply apply the same Chromium build steps to the Metachromium repo. Don't. Google provides its own build system, plugins, config files and dotfiles in the metachromium repo that are crucial for the build process. The path of least resistance is as follows:

1. **Familiarize** yourself with the general process of building Chromium [here](https://www.chromium.org/developers/how-tos/get-the-code). Learning how to build Chromium on your system can be a rocky road; keep in mind 90% of the process of building Metachromium will resemble building Chromium or Chrome.
2. **Follow** the guide up to and including the step called `Get the Code`. 
3. In a separate folder, **clone** this repo, then move or copy its files to the `src` directory in the Chromium repo. 

4. run `gclient sync` in the root folder. This will install additional files necessary for the build process.
5. Follow the process from `Setting Up the Build` onwards. `autoninja -C out\Default chrome` fires off the build process but examine the build setup step and particularly `--filters` for ways to avoid enormous build times and focus on the bits you need from the codebase.

------------

Note: the chromium instructions are somewhat lacking. A few particular pain points you should know about:
- rather than simply `gn`, enter the full path to `gn` where relevant (i.e `..\..\misc\gn\gn.exe gen --ide=vs` etc).
- _Even if you have the Windows 10 SDK installed via the VS Installer, you probably don't have the necessary Debugging Tools installed to use VS with this repo_. However, you can install them from Windows 10's "Apps & Features" menu. See [this Stackoverflow answer](https://stackoverflow.com/questions/46237620/how-to-install-debugging-tools-with-visual-studio-2017-installer) in case you run into related errors.
- webxr implementation-specific code resides in `[root]/third_party/blink/renderer/modules/xr`, although you'll find tests and sample files elsewhere in the repo.
- if any of the steps fail to work, try `gclient sync`ing again.
