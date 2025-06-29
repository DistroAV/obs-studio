OBS Studio <https://obsproject.com>
===================================

This REPO has a UNIQUE purpose :

Allow plugin release / support to continue until a new tag or release is provided on the official OBS Studio project.

# This fork will be phased-out soon

If you used this repo, please update your buildspec.json as follow :
https://github.com/obsproject/obs-plugintemplate/pull/149


## The context & issue
- cmake4 behavior changed for macOS SDK detection.
- The fix is already on the obs-studio master branch but not available in any tagged commit or release (as os 31.0.3)
Soruce : https://github.com/obsproject/obs-studio/pull/11893

- There seems to be no planned hotfix release on 31.0 branches planned.


## What is this fork purpose?
It was the most straight forward without modifying (and testing) the code in the plugin and then revert it back once a new tag is available (with the fix) .

See the details at : https://github.com/DistroAV/DistroAV/pull/1252

## What is 31.0.0-fix?
It the 30.0.0 tagged release with the unique fix to allow for building MacOS (github action) 

Nothing-else.

## How to use it?
This is made here primarily for the DistroAV plugin.
Other plugin can use it if they want following the proposed process below :

Change the buildspec.json from the official upstream to this below:

        "obs-studio": {
            "version": "31.0.0-fix",
            "baseUrl": "https://github.com/distroav/obs-studio/archive/refs/tags",
            "label": "OBS sources",
            "hashes": {
                "macos": "badf8839e65b00d74440d6f7dc2e48639717c6f3709c95be88214775dffde292",
                "windows-x64": "1baf7fbf0bbb3769133572fe4f826c15bbccf498d4d6e2c7f75017c3612590fd"
            }


Can also see the PR on the DistroAV plugin for reference :
https://github.com/DistroAV/DistroAV/pull/1252


### Recommended Optional Steps in your plugin
- Do this in a PR with a clear statement that this is temporary and MUST be reverted : see example at : https://github.com/DistroAV/DistroAV/pull/1252
- Create an issue that this MUST be reverted as soon as there is a new OBS Source release / Tag (after 31.0.3) : See example at : https://github.com/DistroAV/DistroAV/issues/1253


# IMPORTANT
1. No support whatsoever on this will be provided
2. As soon as the tag/release is done on OBS-studio (upstream) - The tags and this repo will be deprecated and ultimately removed.
3. This does not fix your plugin code, and you might still have the cmake compiler error. Check this out if that is the case : https://github.com/obsproject/obs-plugintemplate/pull/145
