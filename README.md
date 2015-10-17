## yocto-repo ##


**yocto-repo** is a Yocto meta repository manifest to allow the use of Google's "repo" to manage a number of Yocto repositories.  
If you are unfamiliar with repo, you can read up on it [here](http://source.android.com/source/version-control.html).  
  
The **yocto** repositories catered for here are

  1.	[yocto](https://www.yoctoproject.org/) itself
  2.	[openembedded](git://git.openembedded.org)
  3.	[fsl-community-bsp-base](https://github.com/Freescale/fsl-community-bsp-base)
  4.	[

### Download and Install Google's repo utility ###

The BSP is based on the Yocto Project, which consists of a number of applicable metadata 'layers'. These are managed by the repo utility.

    $: mkdir ~/bin
    $: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+x ~/bin/repo 


### Create the BSP directory for YOCTO 1.7 fido ###
    
    $: PATH=${PATH}:~/bin
    $: mkdir yocto-fido
    $: cd yocto-fido

#### Initialise the repositories for POKY fido ####

    $: repo init -u https://github.com/noeldiviney/yocto-repo 

#### Download yocto, poky, openembedded and all BSP metadata layers ####

    $: repo sync

once this has completed you should have a complete development environment

##----------------------------------------------------------------------##

### Build a project ie the Wanboard-quad ###
source the environment

    $: source sources/poky/oe-init-build-env builds/Freescale/wandboard-quad/

Run Bitbake

    $: bitbake fsl-image-multimedia-full

##----------------------------------------------------------------------##

### Build a project ie the raspberrypi ###
source the environment

    $: source sources/poky/oe-init-build-env  builds/Raspberrypi/model-b+

Run Bitbake

    $: bitbake rpi-hwup-image
    
