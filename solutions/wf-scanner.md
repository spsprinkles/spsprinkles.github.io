---
layout: default
title:  ""
categories: Solutions
---
![Demo](/images/wf-dashboard.png)

### Overview

Scans site collection(s) for workflow instances.

[Click Here](https://github.com/datta-framework/wf-dashboard) to access the repository.

#### Deployment Guide

Follow the [deployment steps](/jump-start-projects/overview/deployment) based on the target environment.

##### Additional Steps

TODO

1. Access the page containing the solution
   a) Ensure the page is viewed in classic
   b) Click the link in the bottom left to view the page in classic
2. Access the developer tool's console
   a) Press F-12 or Ctrl+Shift+I
   b) Select the console tab
3. Load the script
   `var s = document.createElement("script"); s.src="/sites/dev/siteassets/wf-dashboard/wf-dashboard.min.js"; document.head.appendChild(s);`
4. Install the solution
   `WFDashboard.Configuration.install()`

#### Extending the Solution

The solution can be forked and extended for further client customizations.