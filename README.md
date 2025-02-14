# Dockerfile Bug: Non-zero exit code during npm install

This repository demonstrates a common error encountered when building Node.js applications using Docker.  The `npm install` command within the Dockerfile fails, resulting in a non-zero exit code and preventing the image from building successfully.

The issue stems from the omission of a `package-lock.json` file, or potentially issues with dependency resolution that are not handled gracefully.  This can lead to inconsistent build environments and frustrating debugging.

## Bug

The provided `Dockerfile` attempts to install project dependencies using `npm install`. However, because of the missing `package-lock.json`, or the possibility of problems in the `package.json` file and the version's incompatibilities between the installed packages, the build process will stop.

## Solution

The `Dockerfile-solution` corrects the issue by ensuring both `package.json` and `package-lock.json` are present in the source code. By including the `package-lock.json`, we guarantee a deterministic build environment and resolve any potential discrepancies in dependency versions.