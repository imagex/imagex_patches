## ImageX - Drupal Patches

The following is a collection of patches that are used on a regular basis during active development. This repository exists as a central holding area for all patch files that are applied to Drupal Core, contributed modules and themes. The reasoning for this is the result of [ImageX's Installation Kit](http://github.com/imagex/imagex_installkit) and the Drush make process of using a URL for loading patch files.

### Patches for Drupal Core

#### Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch enables the ability to have inheritable (multiple) profiles allowing for one installation profile to depend on another. Drupal currently supports the inheritable themes or "base themes" but does not support this functionality for profiles. Therefore, this patch was created to be contributed back into the Drupal 7 core, in addition to it solving code management and product architecture problems previously faced.

*Patch File: [1356276-D7-inheritable-profiles-multi.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inheritable-profiles-multi.patch)*

### Patches for Contributed Modules

*There are currently no patches that are being used within active development for contributed modules.*

### Contributing

If you believe that we are missing a patch that should exist and or you have a revised patch that should be updated, please fork the repository, update and create a new pull request. Be sure to include the patch file, a description of what the patch does and why it is necessary.

This repository is maintained by the development leads and their teams at [ImageX](http://imagexmedia.com).