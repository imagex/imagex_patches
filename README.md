# Drupal Patches

The following is a collection of patches that are used on a regular basis during active development. This repository exists as a central holding area for all patch files that are applied to Drupal Core, contributed modules and themes. The reasoning for this is the result of [ImageX's Installation Kit](http://github.com/imagex/imagex_installkit) and the Drush make process of using a URL for loading patch files.

## Patches for Drupal Core

#### Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch enables the ability to have inheritable (multiple) profiles allowing for one installation profile to depend on another. Drupal currently supports the inheritable themes or "base themes" but does not support this functionality for profiles. Therefore, this patch was created to be contributed back into the Drupal 7 core, in addition to it solving code management and product architecture problems previously faced.

***Patch File: [1356276-D7-inheritable-profiles-multi.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inheritable-profiles-multi.patch)***

## Patches for Contributed Modules

#### Features - Issue: 927566, Comment: 72

This patch enhances features method of identifying menu links, ensuring that each menu link is unique. This patch allows menu links with the same URL to be exported and re-created during the installation.

***Patch File: [features-multiple-link-path-927566-72.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features/features-multiple-link-path-927566-72.patch)***

#### Workbench Moderation - Issue: 1314508, Comment: 70

This patch allows for the workbench moderation's transition's permissions to be exported and re-created during the installation. This resolves the `module cannot be null` error that is presented within the the `user_role_grant_permissions` function of the `user.module`.

***Patch File: [1314508-workbench-moderation-features.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/workbench_moderation/1314508-workbench-moderation-features.patch)***

#### Ckeditor - Issue: 1504696, Comment: 58

This is a follow up patch to the one Kevin created to add media 2.x support to ckeditor.

***Patch File: [ckeditor_1504696_58.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ckeditor/ckeditor_1504696_58.patch)***

#### Ckeditor - Issue: 2043365, Comment: 6

This patch fixes a problem where text formats assigned by ckeditor profiles in Features wouldn't be respected when they should be empty.

***Patch File: [ckeditor-ckeditor_features_format-2043365-6.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ckeditor/ckeditor-ckeditor_features_format-2043365-6.patch)***

#### Media Crop - Issue: 2075161, Comment: 2

Small patch removing dependence on the wysiwyg module, since we're using ckeditor instead.

***Patch File: [wysiwyg-dependece-remove_2075161_1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/wysiwyg-dependece-remove_2075161_1.patch)***

#### Media Crop - Issue: 2043365, Comment: 6

This patch fixes a bug where embedded image crop images aren't rendered in Firefox. This is due to a bug where it can't handle multiple iframes in the DOM. This patch adds a try/catch for the right wysiwyg iframe.

***Patch File: [media_crop-access-iframes-safely-1710824-7.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/media_crop-access-iframes-safely-1710824-7.patch)***

#### Media Crop - Issue: 1896860, Comment: 1

This patch makes Media Crop functionality work with Media 2.x. Patch by Shea.

***Patch File: [media_crop-7-x.1.x_media-2.x.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/media_crop-7-x.1.x_media-2.x.patch)***

#### Libraries API - Inheritable Profiles

This patch enables the Libraries API module to take into consideration multiple profiles when performing a libraries directory search. This is a *required* patch if using the Inheritable Profiles patch listed above when using the Libraries API.

***Patch File: [libraries-inheritable-profiles-fix.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/libraries/libraries-inheritable-profiles-fix.patch)***

## How to use these patches

Patches should not be applied directly to the codebase that is committed to repositories as a result of increased effort to update the codebase when a new version of core, contributed modules and or themes are released. Instead, it is recommended that you make use of the `drush make` process and a `drupal-org.make` file for applying patches to projects.

Each of the patch links above directly link to the RAW version of the patch file that is to be applied. The `drush make` files that specify patches for projects using the `projects[project-name][patch][]` syntax need to have a URL specified for the patch file. Therefore, copy the RAW URL of the patch file that lives within this repository and specify it within `drush make` project build file. This will allow for increased management of the code that is to be patched in addition to ease of managing revisions to the patches.

All projects that make use of these patches should also not directly link to the forked repositories RAW version of the patch file but instead directly to this repositories RAW version.

For example, if your project is to have the inheritable profiles patch applied to it, the `drupal-org-core.make` file may look something like this:

```
api = 2
core = 7.x

; Download Drupal core.
projects[drupal][type] = "core"
projects[drupal][version] = "7.23"

; Apply the inheritable profiles patch to core.
projects[drupal][patch][] = https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inheritable-profiles-multi.patch
```

## Contributing

If you believe that we are missing a patch that should exist and or you have a revised patch that should be updated, please fork the repository, update and create a new pull request. Be sure to include the patch file, a description of what the patch does and why it is necessary.

This repository is maintained by the development leads and their teams at [ImageX](http://imagexmedia.com).
