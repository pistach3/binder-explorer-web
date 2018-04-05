# How to run this project

This project has been designed to be integrated inside and AOSP tree. It has been tested on the HiKey 620 board (arm64) and on the x86_64 emulator. It should work with minimal modifications on the ia32 emulator on other arm boards supporting Android.

Before following those steps, you need to use the https://github.com/fdgonthier/Aosp-Node-Prebuilts project so that a Node.js binary is present on your target. Binder Explorer requires Node.js and will not work without it.

If you do not want to setup a Node.js environment, you can download the prebuilt package for the most current version. This package is larger but include all the dependencies required for Binder Explorer to work. The package is available in the Releases section of the GitHub repository. If you use that package, skip the following steps to up until running "mm".

If you do not want or can't use the prebuilt package, you need to setup a working Node.js environment. See https://nodejs.org/en/download/package-manager/ to install it on your computer

If you want to build from source, checkout the project in your AOSP tree.

> git checkout 

Install the required packages:

> $ npm install

Install the required client side package (you might have to install the `bower` npm package)

> $ bower install

Assemble the package to install on the device:

> $ grunt [x86_64|arm64]

Run 'mm' to insert the application on the device

> $ mm

# Running

The application can be run from the ADB shell but you need to forward ports first:

> $ adb forward tcp:3000 tcp:3000

You can then run the application from within the ADB shell:

> $ OsysBE

You can access the app on localhost:3000

The application will output plenty of debugging statements when running.

# Cleaning / Reinstalling

To remove the application from the build:

Remove the launcher

> $ rm out/target/product/[product name]/system/bin/OsysBE

At this point, if you run mm again, the application will be reinstalled on the device. This is how to reinstall the app if you've done modifications.

> $ rm -rf out/target/product/[product name]/system/Osys/BE

# Contributors

* François-Denis Gonthier francois-denis.gonthier@opersys.com -- main developer and maintainer
* Karim Yaghmour karim.yaghmour@opersys.com -- ideas and other forms of entertainment
