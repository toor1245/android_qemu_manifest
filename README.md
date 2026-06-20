# Download AOSP

1. Download android 17 manifest

```shell
repo init \
    -u https://android.googlesource.com/platform/manifest \
    -b android-17.0.0_r1 --depth=1
```

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
