---
layout: howtom2devgde_chapters_fedg
title: Create a theme (general information), draft
---

<h1 id="theme-gen">{{ page.title }}</h1>

<p><a href="{{ site.githuburl }}frontend-dev-guide/themes/theme-general.md" target="_blank"><em>Help us improve this page</em></a>&nbsp;<img src="{{ site.baseurl }}common/images/newWindow.gif"/></p>

<h2 id="theme-gen-overview">Overview</h2>
A theme is a component of Magento application which provides a consistent look and feel (visual design) for entire application area (for example, storefront or Magento admin) using a combination of custom templates, layouts, styles or images. 

Themes are designed to override or customize view layer resources, provided initially by modules or libraries.<!--ADDLINK to Fallback--> Themes are implemented by different vendors (frontend developers) and intended to be distributed as additional packages for Magento system similar to other components.

Out-of-the-box Magento application provides two design themes: Luma, as a demonstration theme, and Blank as a basis for custom theme creation.

There are no restrictions on using the demonstration Luma theme for a live store, but if you want to customize the default design, you need to create a new theme. We strongly recommend not to change the default Luma and Blank theme files, because if you do edit the default files, your changes can be overwritten by the new version of the default files during upgrades.

Your new theme can be a standalone new theme, or can inherit from the default or any other existing one. The theme inheritance logic implemented in the Magento system allows you changing only certain theme files, and inheriting the rest necessary files from a parent theme. <!--ADDLINK Magento Theme Inheritance for details. -->

The How to Create New Theme chapter provides all information, including theoretical concepts and practical references, a frontend developer might need to efficiently create a new theme in Magento application.

<h2 id="theme-gen-walkthrough">Adding new theme: walkthrough</h2>
The high-level steps required to add a new theme in the Magento system are the following:

1. Create a folder for the theme under `app/design/frontend/<your_vendor_name>/<your_theme_name>`.
2. Add a declaration file `theme.xml` and optionally `view.xml` to the theme folder.
3. Add a `composer.json` file.
3. Create folders for CSS, JavaScript, images, and fonts.
4. Configure your theme in the Admin panel.
<h2 id="theme-gen-read">Recommended reading</h2> 

* <a href="https://github.com/magento/magento2/tree/master/app/code/Magento" target="_blank">Checklist of modules</a>
* <a href="{{site.gdeurl}}architecture/view/static-process.html">Static view files processing</a>