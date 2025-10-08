## Introduction ##
- This repository contains a sample Site Initializer Client Extension.
- The Site Initializer will create a new Site if the Site referenced in client-extension.yaml doesn't already exist.
- It creates (or updates) the following design elements within the Site:
  - Web Content Structure: site-initializer\ddm-structures\mw_wcm.xml
  - Web Content Template: site-initializer\ddm-templates\mw_wcm
  - Search Results Widget Template: site-initializer\ddm-templates\custom-search-results
 
## Setup ##
- client-extension.yaml
  - Update the following values to match an existing site (or leave as is to create a new Site):
    - siteExternalReferenceCode: 470b5927-1e36-7764-35d1-b331e77e7894
    - siteName: Site Initializer Test
- Build the Site Initializer Client Extension
- Deploy the Site Initializer Client Extension .zip (LUFFA) file to the osgi/client-extensions folder
- Check the logs, output similar to the following should appear:
```
2025-10-08 13:21:01.368 INFO  [Refresh Thread: Equinox Container: c9deca61-3939-4547-96e6-863a55c21857][BundleSiteInitializer:531] Initializing Site Initializer Test for group 36012
2025-10-08 13:21:01.404 INFO  [Refresh Thread: Equinox Container: c9deca61-3939-4547-96e6-863a55c21857][BundleSiteInitializer:5677] Invoking addOrUpdateListTypeDefinitions took 0 ms
...
...
...
2025-10-08 13:21:02.834 INFO  [Refresh Thread: Equinox Container: c9deca61-3939-4547-96e6-863a55c21857][BundleSiteInitializer:5677] Invoking addOrUpdateResourcePermissions took 1 ms
2025-10-08 13:21:02.843 INFO  [Refresh Thread: Equinox Container: c9deca61-3939-4547-96e6-863a55c21857][BundleSiteInitializer:549] Initialized Site Initializer Test for group 36012 in 1474 ms
```

## Notes ##
- This is sample that is being provided ‘as is’ without any support coverage or warranty.
- This sample should be used in a non-production environment only.
- The Site Initializer Client Extension was created for Liferay DXP 2025.Q1.x.
- The Site Initializer Client Extension will run in each node if it is deployed in multiple nodes of a clustered environment.

## Site Initializer Reference ##
- https://learn.liferay.com/w/dxp/development/importing-exporting-data/site-initializers
- https://learn.liferay.com/w/dxp/development/importing-exporting-data/using-a-site-initializer-client-extension
- Samples
  - https://github.com/liferay/liferay-portal/tree/master/workspaces/liferay-tryitnow-workspace/client-extensions/liferay-tryitnow-site-initializer
  - https://github.com/liferay/liferay-dxp/tree/7.4.13/modules/apps/site-initializer
