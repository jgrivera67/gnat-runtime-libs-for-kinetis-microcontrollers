# gnat-runtime-libs-for-kinetis-microcontrollers

Gnat Ada Runtime libraries for Kinetis Micrcocontrollers.
To use a library from this repository, follow the instructions below.

## ravenscar-sfp-kinetis_kl25z

- Copy the ravenscar-sfp-kinetis_kl25z folder to your `<GNAT-installation-path>/GNAT/2016/arm-eabi/lib/gnat`.
- Since the Kinetis KL25Z MCU has an ARM Cortex-M0+ core, the library needs to be compiled
  using `-mcpu=cortex-m0plu`. However, for some reason, even with specifying -mcpu=cortex-m0plus in 
  `<GNAT-installation-path>/GNAT/2016/arm-eabi/lib/gnat/ravenscar-sfp-frdmkl25z\runtime.xml`,
  the linker links the libgcc for armv7-m instead of the armv6-m libgcc. 
  This causes the wrong __aeabi_idiv to be linked. The armv7-m __aeabi_idiv 
  uses an "ït" instruction which does not exist for cortex-m0+ (armv6-m). This 
  causes the code generated for division expressions to hit a hardware exception  

## ravenscar-sfp-kinetis_k64f

- Copy the ravenscar-sfp-kinetis_k64f folder to your `<GNAT-installation-path>/GNAT/2016/arm-eabi/lib/gnat`.
