Huawei MediaPad FHD10 3.0.8 Kernel
=============================


Source:

Huawei FHD10 Open Source(JellyBean,KitKat,kernel-3.0.8)



Compiling TUTORIAL Linux 64BIT:





cd kernel

export ARCH=arm (select architecture of your phone)
export SUBARCH=arm (select architecture of your phone)
export CROSS_COMPILE=arm-linux-androideabi-4.6/prebuilt/linux-x86_64/bin/arm-linux-androideabi- (tell the Kernel, where your compiler is)
make -j[number of your cpu-cores+1] ARCH=arm (This will start the process .. will take some time)
(if you don't get the zImage try: make -j[number of cpu-cores+1] zImage)
 

Now you have your zImage 

Include of your zImage to boot.img :

Download the Rom you want to use (original is recommendet)

extract the rom

Use Huawei-Update-Extractor to extract boot.img (I used Windows to do so, cause wine doesn't do the job)
(http://forum.xda-developers.com/showthread.php?t=2433454) [sometimes its called 09.boot.img .. then just rename it to boot.img]

Download (http://forum.xda-developers.com/showthread.php?t=2319018)
extract
copy your boot.img to this folder
chmod +x umkbootimg (to make it executable)
chmod +x mkbootimg (to make it executable)

./umkbootimg boot.img

rm zImage (remove the zImage file)

copy your zImage in this folder where the zImage from your boot.img was

./mkbootimg new_boot.img

now you have a boot.img with new kernel
just flash it via fastboot
