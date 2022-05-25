Setup:

```bash
git clone https://github.com/dywisor/genimage-debian genimage-debian
cd genimage-debian
git remote add upstream https://github.com/pengutronix/genimage

apt-get install git-buildpackage build-essential debhelper autoconf pkgconf fakeroot libconfuse-dev
```

Build:

```bash
cd genimage-debian

git pull --ff-only
git fetch upstream

git clean -d --force
gbp buildpackage -uc -us
```

Lintian (replace version):

```bash
PVR=15-1
lintian -i -I --show-overrides ../genimage_${PVR}_amd64.changes
```
