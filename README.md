# LineageOS 23.2 for the Sony Xperia Z3+/Z4, Z5 and Z5 Premium

Local manifests to build LineageOS 23.2 (Android 16) for the Sony Xperia kitakami devices
(Qualcomm MSM8994).

## Devices

| Device | Codename | Models | File | Status |
|---|---|---|---|---|
| Xperia Z3+ / Z4 | ivy | E6533, E6553 | `ivy.xml` | Untested |
| Xperia Z5 | sumire | E6603, E6633, E6653, E6683 | `sumire.xml` | Untested |
| Xperia Z5 Premium | satsuki | E6833, E6853, E6883 | `satsuki.xml` | Tested |

`kitakami-common.xml` is always needed as it carries the common device tree, the kernel, the
vendor blobs, the device HALs and the platform repos that carry changes for these devices.

## Branches

| Branch | Android | Lunch target |
|---|---|---|
| `lineage-23.2` | 16 | `lineage_<codename>-bp4a-user` |
| `lineage-24.0` | 17 | `lineage_<codename>-cp2a-user` |

## Building

```
repo init -u https://github.com/LineageOS/android.git -b lineage-23.2 --git-lfs
git clone https://github.com/LineageOS-Sony-MSM8994/local_manifests -b lineage-23.2 .repo/local_manifests
repo sync -c
source build/envsetup.sh
lunch lineage_<codename>-bp4a-user
mka bacon
```

Replace `<codename>` with `ivy`, `sumire` or `satsuki`.

## Updating

```
git -C .repo/local_manifests pull
repo sync -c
```

If you keep your own changes in any of the synced repos, create the branch with
`repo start`, not `git checkout -b`. A branch with no upstream is dropped to a detached
HEAD on the next `repo sync`, without any error.

## Remotes

| Remote | Points to |
|---|---|
| `msm8994` | [LineageOS-Sony-MSM8994](https://github.com/LineageOS-Sony-MSM8994): forks of LineageOS and AOSP repos with changes for these devices |
| `joseefitness` | [Joseefitness](https://github.com/Joseefitness): device trees, kernel, vendor blobs and display HAL |
| `lineage` | [LineageOS](https://github.com/LineageOS): device dependencies used unmodified |
