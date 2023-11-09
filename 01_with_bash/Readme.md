# With bash!

## Creating the file system structure 
```bash
git submodule update --init --recursive
cd external/toybox && make defconfig 
make all && make install
mkdir ../../01_with_bash/rootfs
cd ../../01_with_bash/rootfs
mv ../../external/install/** ./
mkdir -p {dev,etc/rc,home,mnt,proc,root,sys,tmp/run,var,lib,lib64}
chmod a+rwxt tmp/
ln -s usr/{bin,sbin,lib} tmp/run
cp /bin/bash bin/bash
ldd bin/bash #--> copy shared libraries
ldd bin/toybox #--> copy shared libraries
# some times lib folders are just simlinks so be aware where they point
sudo bin/toybox chroot $(pwd) bin/bash
#done
```