### FSL Community BSP

revised by dj-zhou

To get the BSP, you need to install the  `repo` utility by (command from [`djtools`](https://github.com/dj-zhou/djtools)):

```bash
dj setup google-repo
```

Then, you can do the following :

```bash
cd ~
mkdir fsl-community-bsp-zhou
cd fsl-community-bsp-zhou
repo init -u https://github.com/dj-zhou/fsl-community-bsp-zhou -b rocko
repo sync -j4
```

In the above commands, `rocko` is the branch name, may good for Ubuntu 16.04.

For Ubuntu 18.04, you should use `sumo` or `thud`; for Ubuntu 20.04, you should use `dunfell`.

Start to build a simple image:

```bash
cd ~/fsl-community-bsp-zhou
source poky/oe-init-build-env wandboard
bitbake appolo-image
```

The recipe of `appolo-image` is in `meta-zhou/recipes-zhou/images`.

To revise the manifest without pushing changes to this repository, you can:

```bash
cd ~/fsl-community-bsp-zhou/.repo/manifests
gedit default.xml
```

 For example, you can change `master` to `test-branch`, for testing the branch `test-branch` in `meta-zhou`:

```xml
<project remote="zhou" revision="test-branch" name="meta-zhou" path="meta-zhou"/>
```
