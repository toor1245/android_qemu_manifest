repo init -u https://android.googlesource.com/platform/manifest -b android-17.0.0_r1 --depth=1
curl -o .repo/local_manifests/remove_projects.xml -L https://raw.githubusercontent.com/toor1245/android_qemu_manifest/main/remove_projects.xml --create-dirs
repo sync