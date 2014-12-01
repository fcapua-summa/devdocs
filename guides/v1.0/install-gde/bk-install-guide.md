---
layout: default
group: install
subgroup: Getting Started
title: Installation overview
menu_title: Installation overview
menu_node: parent
menu_order: 1
github_link: install-gde/bk-install-guide.md
---

This guide discusses how to install Magento and extensions using Composer. 

<h2 id="instgde-overview-composer">Composer and Magento</h2>

We now use <a href="https://getcomposer.org/" target="_blank">Composer</a> to install the Magento 2 software. Composer enables us to manage Magento 2, extensions, and their dependencies.

Composer provides you with the following advantages:

*	Enables you to reuse third-party libraries without bundling them with source code
*	Component-based architecture with robust dependency management
*	Manages dependencies to reduce extension conflicts and compatibility issues
*	Versioned dependencies
*	<a href="https://getcomposer.org/doc/01-basic-usage.md#package-versions" target="_blank">Semantic versioning</a>
*	Supports PHP Framework Interoperability standard

We'll have more information soon on how developers can use Composer to package extensions to distribute to Magento merchants and to other developers.

<h2 id="instgde-overview-roadmap">High-level installation roadmap</h2>

Following is a brief overview of how to install the Magento 2 software.

<h3>Step 1: Verify your prerequisites</h3>

Use the following table to verify you have the correct prerequisites to install the Magento 2 software.

<table>
	<tbody>
		<tr>
			<th>Prerequisite</th>
			<th>How to check</th>
			<th>For more information</th>
		</tr>
	<tr>
		<td>Apache 2.2 or later</td>
		<td>Ubuntu: <code>apache -v</code><br>
		CentOS: <code>httpd -v</code></td>
		<td><a href="{{ site.gdeurl }}install-gde/prereq/apache.html">Apache</a></td>
	</tr>
	<tr>
		<td>PHP 5.4.11 or 5.5.x</td>
		<td><code>php -v</code></td>
		<td><a href="{{ site.gdeurl }}install-gde/prereq/php-ubuntu.html">PHP Ubuntu</a><br><a href="{{ site.gdeurl }}install-gde/prereq/php-centos.html">PHP CentOS</a></td>
	</tr>
	<tr><td>MySQL 5.6.x</td>
	<td><code>mysql -u [root user name] -p</code></td>
	<td><a href="{{ site.gdeurl }}install-gde/prereq/mysql.html">MySQL</a></td>
	</tr>
</tbody>
</table>

<h3>Step 2: Prepare to install</h3>

After verifying your prerequisites, perform the following tasks in order to prepare to install the Magento 2 software.

1.	<a href="{{ site.gdeurl }}install-gde/install/composer-clone.html#instgde-prereq-compose-install">Installing Composer</a>
2.	<a href="{{ site.gdeurl }}install-gde/install/composer-clone.html#instgde-prereq-compose-clone">Cloning the Magento 2 GitHub repository</a>
	
<h3>Step 3: Installing and verifying</h3>

1.	<a href="{{ site.gdeurl }}install-gde/install/prepare-install.html">Updating installation dependencies</a>
1.	<a href="{{ site.gdeurl }}install-gde/install/install-web.html">Running the web-based installer</a>
2.	<a href="{{ site.gdeurl }}install-gde/install/install-cli.html">Running the command-line installer</a>
2.	<a href="{{ site.gdeurl }}install-gde/install/verify.html">Verifying the installation</a>

<h2>Required server permissions</h2>

Unless otherwise noted, all commands in this guide must be entered as a user with `root` privileges and permission to write to the web server docroot. Depending on your system, that might mean you must use different user accounts or add users to the web server user group&mdash;provided that group has sufficient privileges.

Installing software on Linux typically requires `root` privileges. You should generally not install the Magento 2 software in the web server docroot using `root` privileges; however, that is up to you.