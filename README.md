# Kenvyra

An open-source Android ROM project with performance in mind.

Brought to you by the former DavinciCodeOS team.

## Building

Building the ROM requires you to initialize the manifest first, like so:

```bash
mkdir kenvyra
cd kenvyra
repo init -u https://github.com/itsHanibee/kenvyra_manifest.git -b kenvyra-13.0
```

For unofficial builds, you will have to manually add device trees and kernel, here's a simple way to clone the trees for chime:

```bash
git clone https://github.com/itsHanibee/device_xiaomi_chime -b kenvyra-13 device/xiaomi/chime
git clone --depth=1 https://github.com/itsHanibee/kernel_xiaomi_chime -b android kernel/xiaomi/chime
git clone https://github.com/BootleggersROM-Devices/vendor_xiaomi_chime vendor/xiaomi/chime
git clone https://github.com/LineageOS/android_hardware_xiaomi -b lineage-20 hardware/xiaomi
```

Now, download the sources:

```bash
repo sync -c -j4 --jobs-checkout=$(nproc --all) --force-sync --no-clone-bundle --no-tags --optimized-fetch
```

It's time to start building. (Again, this is for chime.)

```bash
# For GApps
source build/envsetup.sh
export KENVYRA_GAPPS=true
lunch kenvyra_chime-userdebug
make bacon
```

## Credits

- LineageOS team for the base
