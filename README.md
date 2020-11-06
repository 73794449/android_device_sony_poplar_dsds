Device configuration for Sony Xperia XZ1 dual sim variant (poplar_dsds)
========================================================

Description
-----------

This repository is for AOSPA ruby on Sony Xperia XZ1 dual sim variant (poplar_dsds).

How to build AOSPA ruby
----------------------

* Make a workspace:

        mkdir -p ~/aospa
        cd ~/aospa

* Initialize the repo:

        repo init -u https://github.com/AOSPA/manifest -b ruby

* Create a local manifest:

        cd .repo & mkdir local_manifests
        cd local_manifests & nano roomservice.xml
        
<?xml version="1.0" encoding="UTF-8"?>
        <manifest>
                <!-- SONY -->
        <project name="T3RY4/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="aospa-ruby" />
        <project name="T3RY4/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="aospa-ruby" />
        <project name="T3RY4/android_device_sony_poplar_dsds" path="device/sony/poplar_dsds" remote="github" revision="aospa-ruby" />
                <!-- Pinned blobs for poplar_dsds -->
        <project name="T3RY4/android_vendor_sony_poplar_dsds" path="vendor/sony/poplar_dsds" remote="github" revision="aospa-ruby" />
        </manifest>

* Sync the repo:

        repo sync -f --force-sync --no-clone-bundle

* Extract vendor blobs

        cd device/sony/poplar_dsds
        ./extract-files.sh ~/path/to/blobs

* Setup the environment

        source build/envsetup.sh
        lunch aospa_poplar_dsds-userdebug

* Build AOSPA ruby

        # Go to the root of the source tree...
        $ cd WORKSPACE
        # ...and run the builder tool.
        $ ./rom-build.sh poplar_dsds
