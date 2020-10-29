Device configuration for Sony Xperia XZ1 dual sim variant (poplar_dsds)
========================================================

Description
-----------

This repository is for Resurrection Remix OS Q on Sony Xperia XZ1 dual sim variant (poplar_dsds).

How to build Resurrection Remix OS Q
----------------------

* Make a workspace:

        mkdir -p ~/rr
        cd ~/rr

* Initialize the repo:

        repo init -u https://github.com/ResurrectionRemix/platform_manifest.git -b Q

* Create a local manifest:

        cd .repo & mkdir local_manifests
        cd local_manifests & nano roomservice.xml
        
<?xml version="1.0" encoding="UTF-8"?>
        <manifest>
                <!-- SONY -->
        <project name="T3RY4/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="rr-q" />
        <project name="T3RY4/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="rr-q" />
        <project name="T3RY4/android_device_sony_poplar_dsds" path="device/sony/poplar_dsds" remote="github" revision="rr-q" />
                <!-- Pinned blobs for poplar_dsds -->
        <project name="T3RY4/android_vendor_sony_poplar_dsds" path="vendor/sony/poplar_dsds" remote="github" revision="rr-q" />
        </manifest>

* Sync the repo:

        repo sync -f --force-sync --no-clone-bundle

* Extract vendor blobs

        cd device/sony/poplar_dsds
        ./extract-files.sh ~/path/to/blobs

* Setup the environment

        source build/envsetup.sh
        lunch rr_poplar_dsds-userdebug

* Build Resurrection Remix OS Q

        make -j(number of threads) bacon
