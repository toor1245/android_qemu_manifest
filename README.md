## Download AOSP

1. Download android 17 manifest

```shell
repo init \
    -u https://android.googlesource.com/platform/manifest \
    -b android-17.0.0_r1 --depth=1 \
    --partial-clone \
    --clone-filter=blob:none \
    -g default,-darwin,-windows
```

- --depth=1: Only fetches the very latest commit, ignoring years of history.
- --partial-clone --clone-filter=blob:none: Downloads the git tree structure but skips downloading the actual file contents until the moment checkout needs them.
- -g default,-darwin,-windows: Instructs repo at the manifest level to completely ignore Mac and Windows prebuilts.
- -c --no-clone-bundle --no-tags: Syncs only the current branch and ignores heavy server-side bundles and tags.

2. Download device/generic/qemu manifest 

```shell
curl -o .repo/local_manifests/manifest_qemu.xml \
    -L https://raw.githubusercontent.com/toor1245/android_qemu_manifest/android-17.0/manifest_qemu.xml \
    --create-dirs
```

3. Remove redundant projects

```shell
curl -o .repo/local_manifests/remove_projects.xml \
    -L https://raw.githubusercontent.com/toor1245/android_qemu_manifest/android-17.0/remove_projects.xml
```

4. Download project

```shell
repo sync
```

### Note:

Delete any projects that are no longer defined in the manifest

```shell
repo sync -c --prune --force-sync
```
