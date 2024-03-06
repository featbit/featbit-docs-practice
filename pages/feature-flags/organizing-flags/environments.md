# Environments

## Overview

This topic explains what environments are in FeatBit and how to use them to manage different business areas or areas of your product lifecycle.

Environments are organizational units contained within projects. Environments allow you to manage your feature flags throughout your entire development lifecycle, from local development through production. Typical environments within a project could be Production, QA, Staging, or individual environments.

You can create multiple environments within each project, and all projects must have at least one environment. To learn more about projects, read [Projects](projects.md).

## Understanding environments

Your first project has two environments, Dev and Prod, by default. Each environment has its own secret, which is used to connect the FeatBit SDK to a specific environment.

## Switching environments

There is an area that shows you the current organization, projects and environment in the top-right corner. Click on the project or environment or switch button allows you to quickly switch between projects and environments.

![](../../feature-flags/assets/organizing-flags/environments/001.webp)

## Manage environments

You can manage your environments from the **Projects** page.

1. Navigate to the **Organization** page.
2.  Click the **Projects** tab.

![](../../feature-flags/assets/organizing-flags/environments/002.webp)

Here are a few things you can do:

* add new environments to a project by clicking **Add environment**
* delete an existing environment by clicking **Remove**, you cannot delete the current environment.
* Update existing environment by clicking **Edit**

## Migrating content between environments

You can migrate some, but not all, content between environments from the flags list. To learn more, read [Copying feature flags](the-flags-list.md#copying-feature-flags).
