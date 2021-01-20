### FSL Community BSP

revised by dj-zhou

#### Build an Image

To get the BSP, you need to install the  `repo` utility by (command from [`djtools`](https://github.com/dj-zhou/djtools)):

```bash
dj setup google-repo
```

Then, you can do the following (take `dunfell` branch as an example):

```bash
cd ~
mkdir yocto-fsl-community-bsp
cd yocto-fsl-community-bsp
repo init -u https://github.com/dj-zhou/yocto-fsl-community-bsp -b dunfell
repo sync -j4
```

In the above commands, `dunfell` is the branch name, it is good for Ubuntu 20.04  host system.

For Ubuntu 18.04, you should use `sumo` or `thud`; for Ubuntu 16.04, you should use `rocko`.

Start to build a simple image `appolo-image`, which is defined in `meta-zhou/recipes-zhou/images`:

```bash
cd ~/yocto-fsl-community-bsp
source poky/oe-init-build-env wandboard-zhou
```

Before `bitbake` the image, we need to use the sample config fies from `meta-zhou`:

```bash
cp ../meta-zhou/conf/local.conf.sample conf/
cp ../meta-zhou/conf/bblayers.conf.sample conf/
```

In `conf/local.conf` file, make sure the paths for `DL_DIR` and `SSTATE_DIR`  are available.

then, we can build the image by:

```bash
bitbake appolo-image
```

### Some Tips

To revise the manifest without pushing changes to this repository, you can:

```bash
cd ~/yocto-fsl-community-bsp/.repo/manifests
gedit default.xml
```

 For example, you can change `master` to `test-branch`, for testing the branch `test-branch` in `meta-zhou`:

```xml
<project remote="zhou" revision="test-branch" name="meta-zhou" path="meta-zhou"/>
```
