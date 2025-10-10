## Introduction ##
- The Site Initializer Client Extension type can be used to create or update content and design elements in a new or existing Liferay DXP Site.
  - Supported content types include Pages, Web Content Articles, Documents and Media Documents.
  - Supported design elements include Web Content Structures and Templates, Widget Templates, Information Templates, Notification Templates, Master Page Templates and Fragments.
- This repository contains a Client Extension (CX) project called 'mw-site-initializer' which contains the following sample design elements:
  - A sample Web Content Structure defined in site-initializer\ddm-structures\mw_wcm.xml file.
  - A sample Web Content Template (for the above sample Web Content Structure) defined in site-initializer\ddm-templates\mw_wcm folder.
  - A sample Search Results Widget Template defined in site-initializer\ddm-templates\custom-search-results folder.
- The CX project defines 2 Client Extensions in the client-extension.yaml:
  - type: siteInitializer - the sample Site Initialize CX.
  - type: oAuthApplicationHeadlessServer - the OAuth 2 Headless Server CX used by the Site Initializer CX.
- When it runs, the Site Initializer will do the following:
  - Create a new Site IF the target Site doesn't already exist. (If the target Site already exists then it skips this step.)
  - Use 'UPSERT' operations (i.e. create or update as needed) for the design elements above.

## Site Initializer and Local Live Staging ##
- To use with Local Live Staging it is necessary to point the Site Initializer to the Global Site.
- The Local Live Site and the Local Live Staging Site share Site Name and Site ERC, so pointing the Site Initializer directly at the Local Live enabled Site will create the artifacts directly in 'Live' only, and not in 'Staging'.
  
## Setup ##
- client-extension.yaml
  - Update the following values to match an existing site (or leave as is to create a new Site):
    - siteExternalReferenceCode: 470b5927-1e36-7764-35d1-b331e77e7894
    - siteName: Site Initializer Test
- Build the Site Initializer CX
- Deploy the Site Initializer CX .zip (LUFFA) file to the osgi/client-extensions folder
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
- This sample Site Initializer CX was created for Liferay DXP 2025.Q1.x.
- A Site Initializer CX will run in each node it is deployed to a clustered Liferay DXP environment.
- A Site Initializer CX project can contain a single SiteInitializer CX and the matching oAuthApplicationHeadlessServer CX only.
- A Site Initializer CX project LUFFA zip file is tied to a single specific target Site.
- To add or update content or design elements in multiple Sites then a unique CX project LUFFA zip file per Site is required.
  - Each should have it's own configured client-extension.yaml and design elements and each must be built and deployed for the changes to be applied in the Liferay system.

## Site Initializer Reference ##
- https://learn.liferay.com/w/dxp/development/importing-exporting-data/site-initializers
- https://learn.liferay.com/w/dxp/development/importing-exporting-data/using-a-site-initializer-client-extension
- https://learn.liferay.com/w/dxp/development/importing-exporting-data/using-a-site-initializer-client-extension/site-initializer-yaml-configuration-reference
- Samples
  - https://github.com/liferay/liferay-portal/tree/master/workspaces/liferay-tryitnow-workspace/client-extensions/liferay-tryitnow-site-initializer
  - https://github.com/liferay/liferay-dxp/tree/7.4.13/modules/apps/site-initializer
