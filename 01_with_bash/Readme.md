mkdir rootfs
cd rootfs
mkdir -p {dev,etc/rc,home,mnt,proc,root,sys,tmp/run,usr/{bin,sbin,lib},var}
chmod a+rwxt tmp/
ln -s usr/{bin,sbin,lib} tmp/run
