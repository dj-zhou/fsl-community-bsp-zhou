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

Start to build a simple image:

```bash
cd ~/fsl-community-bsp-zhou
source poky/oe-init-build-env
bitbake core-image-minimal
```

