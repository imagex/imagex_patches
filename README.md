# Drupal Patches

The following is a collection of patches that are used on a regular basis during active development. This repository exists as a central holding area for all patch files that are applied to Drupal Core, contributed modules and themes. The reasoning for this is the result of [ImageX's Installation Kit](http://github.com/imagex/imagex_installkit) and the Drush make process of using a URL for loading patch files.

## Patches for Drupal Core

#### Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

##### Standard dependency check

This patch enables the ability to have inheritable (multiple) profiles allowing for one installation profile to depend on another. Drupal currently supports the inheritable themes or "base themes" but does not support this functionality for profiles. Therefore, this patch was created to be contributed back into the Drupal 7 core, in addition to it solving code management and product architecture problems previously faced.

***Patch File: [1356276-D7-inheritable-profiles-multi.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inheritable-profiles-multi.patch)***

##### Deep dependency check

This patch is derived from that of the inheritable profiles, however performs a deep dependency check for all modules, not just those listed within a profile's `.info` file.

***Patch File: [1356276-D7-inheritable-profiles-multi-enforce-dependencies.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/inheritable-profiles/1356276-D7-inhertiable-profiles-multi-enforce-dependencies.patch)***

#### File Field - Issue: 2066275

Fixes the file field properties from being overwritten on load.

***Patch File: [2066275-file-field-load-merge-order.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/2066275-file-field-load-merge-order.patch)***

#### File Field (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch ensures that the file field presave hook implementation does not perform a `file_save` should `file_load` return FALSE.

***Patch File: [file_field_presave-file-load-check.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/file_field_presave-file-load-check.patch)***

#### Menu Translation - Issue: 951098, Comment: 50

This patch resolves the PHP Notice errors stating that `tab_root_map` is an undefined variable in the `_menu_translate` function located at `includes/menu.inc.`.

***Patch File: [undefined-menu-translate-notice-951098-50.patch](https://raw.github.com/imagex/imagex_patches/7.x/core/undefined-menu-translate-notice-951098-50.patch)***

## Patches for Contributed Modules

#### Answers

Fixes incorrect `hook_theme` usage of Drupal 6 option `original hook` which results in constant PHP notice warning when overriding the `node--answer.tpl` file.

Applies to 3.x branch.

***Patch File: [answers_base-hook-fix.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/answers/answers_base-hook-fix.patch)***

#### Ckeditor - Issue: [2159403](http://drupal.org/node/2159403), Comment: 6

This patch alters the [Ckeditor](http://drupal.org/project/ckeditor) module to allow for media 2.x-dev support. Media refactored ckeditor wysiwyg support into media_wysiwyg submodule.

Applies to 1.x dev branch from commit 57245a9.

***Patch File: [ckeditor-accomodate-latest-media-changes-2159403-6.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ckeditor/ckeditor-accomodate-latest-media-changes-2159403-6.patch)***

#### Ckeditor - Issue: [1649464](http://drupal.org/node/1649464), Comment: 9

This patch alters the [Ckeditor](http://drupal.org/project/ckeditor) module to integrate settings for the media browser configurations.

Applies to 1.x dev branch from commit 57245a9.

***Patch File: [ckeditor-hook_into_media_admin-1649464-9.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ckeditor/ckeditor-hook_into_media_admin-1649464-9.patch)***

#### Ckeditor - Issue: [2043365](http://drupal.org/node/2043365), Comment: 6

This patch fixes a problem where text formats assigned by ckeditor profiles in Features wouldn't be respected when they should be empty.

***Patch File: [ckeditor-ckeditor_features_format-2043365-6.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ckeditor/ckeditor-ckeditor_features_format-2043365-6.patch)***

#### Composer Manager

This patch alters the version of the [Drupal Composer module](http://drupal.org/project/composer) that is downloaded from the 8.x major version to the *7.x-1.x-dev*.

***Patch File: [composer_manager-drush_dl_composer_ver_7.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/composer_manager/composer_manager-drush_dl_composer_ver_7.patch)***

#### Crazyegg - Issue: 1317938, Comment: 9

This patch alters the [Crazyegg](http://drupal.org/project/crazyegg) module to enable the ability for Crazyegg to be enabled/disabled on a per-page basis using standard Drupal visibility settings. The patch is based off of work done in the [Crazyegg issue dedicated to this feature](https://drupal.org/node/1317938). The patch should be applied to the *1.0* version of the module.

***Patch File: [crazyegg-per_page_activation-1317938-9.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/crazyegg/crazyegg-per_page_activation-1317938-9.patch)***

#### Ctools - Issue: 1828534, Comment: 5

This patch alters the [Ctools](http://drupal.org/project/ctools) module to to fix a warning "Trying to get property of non-object". The patch is taken from work done in an [issue dedicated to this error](https://drupal.org/node/1828534).

Applies to the 1.3 version of Ctools.

#### Ctools - Issue: 1787898, Comment: 7

This patch alters the [Ctools](http://drupal.org/project/ctools) module to to fix a warning "Notice: Undefined property: views_plugin_display_default::$panel_pane_display in views_content_views_panes_content_type_render() ". The patch is taken from work done in an [issue dedicated to this error](https://drupal.org/node/1787898).

Applies to the 1.3 version of Ctools.

***Patch File: [ctools-non-object-warning-1828534-5.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/ctools/ctools-non-object-warning-1828534-5.patch)***

#### Features - Issue: 927566, Comment: 72

This patch enhances features method of identifying menu links, ensuring that each menu link is unique. This patch allows menu links with the same URL to be exported and re-created during the installation.

Applies to the 2.0-rc2 version of Features.

***Patch File: [features-multiple-link-path-927566-72.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features/features-multiple-link-path-927566-72.patch)***

#### Features - Issue: 5430938, Comment: 81

This patch enhances features by providing a new alter hook `hook_features_export_render_alter` which allows the final features code to be altered by being saved to file.
Related issue: [https://drupal.org/comment/5430938](https://drupal.org/comment/5430938)

Applies to the 2.x version of Features.

***Patch File: [features-1317054-81.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features/features-1317054-81.patch)***

#### Features Override - Issue: 1970474, Comment: 5

This patch solves a PHP notice error that identifies an array to string conversion that occurs when viewing the features/features_override page. The error also affects the visual representation of the exports.

***Patch File: [features_override-php_array_to_string_notice-1970474.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/features_override/features_override-php_array_to_string_notice-1970474.patch)***

#### Feeds - Issue: 1989196

This patch alters the [Feeds](http://drupal.org/project/feeds) module to resolve a bug related to its integration with the way date_ical module passes FeedsDateTime objects. This patch eliminates PHP errors related to passing an object to a function expecting a string. At a high level, this patch enables the ability to retrieve and map dates from iCal feeds to Drupal date fields when using an iCal feed as a Feeds source.

Applies to the 2.0-alpha8 version of Feeds.

***Patch File: [feeds_1989196-feedsdatetime-check.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/feeds/feeds_1989196-feedsdatetime-check.patch)***

#### Feeds JSONPath Parser  - Issue: 1083234, Comment: 14

This patch alters the [Feeds JSONPath Parser](http://drupal.org/project/feeds_jsonpath_parser) module to provide libraries support for the jsonpath library.

Applies to the latest 1.x HEAD development version of Feeds JSONPath Parser as of November 5, 2013.

***Patch File: [feeds_jsonpath_parser-libraries-1083234-14.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/feeds_jsonpath_parser/feeds_jsonpath_parser-libraries-1083234-14.patch)***

#### Google Custom Search Engine

This patch alters the [Google Custom Search Engine](http://drupal.org/project/google_cse) module to add autocomplete functionality to search form fields, removes watermark styling from search form fields, and adds 100% width and height styling to search results listing.

Applies to the latest 1.x-dev HEAD of google_cse (commit: 242906103925fca7025d3a12899830a0555521ce)

***Patch File: [google_cse-add_autocomplete_and_styling_changes.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/google_cse/google_cse-add_autocomplete_and_styling_changes.patch)***

#### History.js - Issue: 1964460, Comment: 1

This patch updates the library source repo from https://github.com/balupton/History.js to https://github.com/browserstate/history.js and library path

Applies to 7.x-1.0

***Patch File: [history_js-new_repo-1964460-1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/history_js/history_js-new_repo-1964460-1.patch)***

#### Libraries API - Inheritable Profiles (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch enables the Libraries API module to take into consideration multiple profiles when performing a libraries directory search. This is a *required* patch if using the Inheritable Profiles patch listed above when using the Libraries API.

***Patch File: [libraries-inheritable-profiles-fix.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/libraries/libraries-inheritable-profiles-fix.patch)***

#### Media - Issue: 2071073, Comment: 1

This patch resolves the PHP Warning errors that are presented when the `media_file_default_displays_alter()` function is invoked when comparing an export to the database.

***Patch File: [media-warnings-creating-default-object-from-emtpy-value-2071073-1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media/media-warnings-creating-default-object-from-emtpy-value-2071073-1.patch)***

#### Media - Issue: [2126755](http://drupal.org/node/2126755), Comment: 58

This patch alters the [Media](http://drupal.org/project/media) module to improve macro handling for media elements so that they can more accurately be tokenized and untokenized when the editor binds and unbinds. This is more relevant for ckeditor module now because of refactoring that occurred to more tightly integrate media handling for ckeditor module with that done for wysiwyg module located in media_wysiwyg submodule.

Applies to 2.x dev branch from commit 2f828ea761103c49197a50aaeac9b98a350a559b.

***Patch File: [media-wysiwyg-improve-our-macro-handling-2126755-58.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media/media-wysiwyg-improve-our-macro-handling-2126755-58.patch)***

#### Media - Issue: [2177893](http://drupal.org/node/2177893), Comment: 2

This patch alters the [Media](http://drupal.org/project/media) module to remove the mediawrapper custom wrapper for versions of ckeditor library >= 4.0 that don't have the widgets plugin included in the library (you have to manually build the library to include widgets plugin). The handling of this custom wrapper was breaking tokens in certain instances.

Applies to 2.x dev branch from commit 2f828ea761103c49197a50aaeac9b98a350a559b.

***Patch File: [media-ckeditor-remove-mediawrapper-2177893-2.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media/media-ckeditor-remove-mediawrapper-2177893-2.patch)***

#### Media Crop - Issue: 2075161, Comment: 2

Small patch removing dependence on the wysiwyg module, since we're using ckeditor instead.

***Patch File: [wysiwyg-dependece-remove_2075161_1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/wysiwyg-dependece-remove_2075161_1.patch)***

#### Media Crop - Issue: 2043365, Comment: 6

This patch fixes a bug where embedded image crop images aren't rendered in Firefox. This is due to a bug where it can't handle multiple iframes in the DOM. This patch adds a try/catch for the right wysiwyg iframe.

***Patch File: [media_crop-access-iframes-safely-1710824-7.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/media_crop-access-iframes-safely-1710824-7.patch)***

#### Media Crop - Issue: 1896860, Comment: 1

This patch makes Media Crop functionality work with Media 2.x. Patch by Shea.

***Patch File: [media_crop-7-x.1.x_media-2.x.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/media_crop/media_crop-7-x.1.x_media-2.x.patch)***

#### Panels - Issue: 1480366, Comment: 5

Fixes notice warning with mini panels when clearing the Drupal cache.

***Patch File: [panels-mini-panels-cache-1480366-5.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/panels/panels-mini-panels-cache-1480366-5.patch)***

#### Panels Accordion - Issue: 1965770, Comment: 0

This patch alters the [Panels Accordion](http://drupal.org/project/panels_accordion) module to improve the content editor administration of panels accordions so that an entire region can easily be rendered as an accordion.

Applies to the 1.x-dev HEAD version of the module.

***Patch File: [panels_accordion-remove_pane_style-1965770-0.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/panels_accordion/panels_accordion-remove_pane_style-1965770-0.patch)***

#### Panelizer Permissions - Issue 1968876, Comment: 10

This patch exposes the "allow panels
choice" to permissions, as opposed to anyone having access that can edit the node.

***Patch File: [panelizer-choice_permission_check_display_mode.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/panelizer/1968876-10-panelizer-choice_permission_check_display_mode.patch)***

#### Mini Panels In-Place Editor (panels_mini_ipe) - Issue 1966204

This patch only determines if an object is set using isset().

***Patch File: [panels_mini_ipe-new_custom_content.patch](https://raw2.github.com/imagex/imagex_patches/7.x/contrib/panels_mini_ipe/panels_mini_ipe-new_custom_content.patch)***

#### Path Breadcrumbs

This patch alters the [Path Breadcrumbs](http://drupal.org/project/path_breadcrumbs) module to changes some of the validation checks in code and in form validation handler. It removes the right_value validation check in the path_breadcrumbs_ui module and adds some boolean checks to remove PHP errors.

Applies to the 7.x-3.0-beta6 version of this module.

***Patch File: [path_breadcrumbs-validation_changes.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/path_breadcrumbs/path_breadcrumbs-validation_changes.patch)***

#### Taxonomy Access Fix - Issue: 1637446 (developed by [@amcgowanca](http://github.com/amcgowanca))

This patch allows for the permissions created by the Taxonomy Access Fix module to identify the vocabularies using the machine name of the vocabulary and not the vocabulary id. This patch also provides an update path for existing permissions stored within the `{role_permission}` table.

***Patch File: [taxonomy_access_fix-changes-vocab-vid-to-machinename-usage-1637446.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/taxonomy_access_fix/taxonomy_access_fix-changes-vocab-vid-to-machinename-usage-1637446.patch)***

#### Twitter - Issue: 2142177 (developed by [@kevinchampion](http://github.com/kevinchampion))

This patch alters the [Twitter](http://drupal.org/project/twitter) module to add a missing API hook invocation.

Applies to 6.0-alpha2

***Patch File: [twitter-2142177-1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/twitter/twitter-2142177-1.patch)***

#### UUID Features - Issue: 2072943, Comment: 1

This patch resolves the issue with the Features UI attempting to display the Bean's Title. However, Bean's are not required to have titles and therefore replaces it with the Bean's delta.

***Patch File: [uuid_features-bean-titles-2072943-1.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/uuid_features/uuid_features-bean-titles-2072943-1.patch)***

#### UUID Features - File Field Import (developed by [@amcgowanca](http://github.com/amcgowanca))

***Patch File: [invalid-argument-foreach-var-field.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/uuid_features/invalid-argument-foreach-var-field.patch)***

#### UUID Features - Panelizer (developed by [@arcaneadam](http://github.com/arcaneadam))

This patch adds support in uuid_features for panelizer entities. This allows panelized entities that were exported using uuid to be imported and have their panelized content updated with the new entity_id and inserted into the Database.

***Patch File: [uuid_panelizer.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/uuid_features/uuid_panelizer.patch)***

#### Workbench Access - Issue: 1996418, Comment: 13

This patch alters the [Workbench Access](http://drupal.org/project/workbench_access) module to add an admin configuration setting that allows users to edit a node's menu item even if they don't have the administer menus permission. When workbench_access schema is set to use menu/s to define the access sections, it can be configured to rely on the content's actual menu item placement to define the node's section. In order to do this the content editor needs permission to place the node in the menu in question. The default menu permissions are too broad and can create situations where the user has too much permission.

Applies to 1.x-dev

***Patch File: [workbench_access-1996418-13.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/workbench_access/workbench_access-1996418-13.patch)***

#### Workbench Moderation - Issue: 1314508, Comment: 70

This patch allows for the workbench moderation's transition's permissions to be exported and re-created during the installation. This resolves the `module cannot be null` error that is presented within the the `user_role_grant_permissions` function of the `user.module`.

***Patch File: [1314508-workbench-moderation-features.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/workbench_moderation/1314508-workbench-moderation-features.patch)***

#### Workbench Moderation - Feature Import Errors

This patch fixes a bug that prevents content from being imported with features_uuid that use workbench_moderation

***Patch File: [workbench_moderation.patch](https://raw.github.com/imagex/imagex_patches/7.x/contrib/workbench_moderation/workbench_moderation.patch)***

## Patches for Contributed Themes

#### Mothership - Issue: 2033235, Comment: 16

See https://drupal.org/node/2033235

The current version of Mothership (7.x-2.10) doesn't properly wrap the views template with the views classes. This breaks ajax functionality.

This patch will fix that problem by reinserting the views classes.

***Patch File: [Add-views-classes-2033235-16.patch](https://raw.github.com/imagex/imagex_patches/7.x/themes/mothership/Add-views-classes-2033235-16.patch)***

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
