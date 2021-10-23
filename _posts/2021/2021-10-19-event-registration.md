---
date: 2021-10-19
layout: post
title: Event Registration
subtitle: 
description: An event registration solution designed for SharePoint 2013/Online environments.
image: /assets/posts/event-registration/view-solution.png
optimized_image: /assets/posts/event-registration/view-solution.png
category: solutions
tags:
  - Classic
  - Modern
  - Solutions
author: gunjandatta
---

A tool for organizers to create and manage events in SharePoint Online.

**Original Developers**
_Michael Wilson & Josh Gardner_

## Solution Code

The solution is designed to be used as is or further customized. [Click here](https://github.com/spsprinkles/event-registration) to access the code repository. This solution builds on top of the [Basic Dashboard](https://dattabase.com/examples/#basic-dashboard) walkthrough. To create your own the instance of the solution, follow the steps below.

1. [Fork the solution](https://github.com/spsprinkles/event-registration) and clone it to your machine
2. Install the libraries: `npm i`
3. Link TypeScript: `npm link typescript`
4. Build the Solution: `npm run all`

# Installation and Deployment

## Upload Assets

_Right click and save the files for the next step._

<table>
  <thead>
    <tr>
      <th>Assets</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <a href="https://github.com/spsprinkles/event-registration/raw/master/dist/event-registration.min.js">event-registration.min.js</a>
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/spsprinkles/event-registration/raw/master/assets/eventreg-config.json">eventreg-config.json</a>
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/spsprinkles/event-registration/raw/master/assets/index.html">index.html</a>
      </td>
    </tr>
  </tbody>
</table>

* Go to Site content -> Site Assets where the app shall live
* Create a new folder and it _must_ be named `event-registration`

![image](/assets/posts/event-registration/create-folder.png)

* Click inside of the folder and upload the following:

![image](/assets/posts/event-registration/upload-assets.png)

## Create WebPart Page

* Navigate to Site Pages

![image](/assets/posts/event-registration/site-pages.png)

* Click New -> Web Part Page
* Type the name of the page before ".aspx" (era is recommended) and select "Full Page, Vertical" for layout template.

![image](/assets/posts/event-registration/create-wp.png)

* Navigate to the `Site Assets` library and move the file to the `event-registration` folder

![image](/assets/posts/event-registration/move-file.png)

* Navigate to the page and click on it to view it
* Click on the `Edit` button

![image](/assets/posts/event-registration/edit-page.png)

## Configure Solution

* Click "Add a Web Part" and set Categories to "Media and Content" and Parts to "Content Editor"

![image](/assets/posts/event-registration/add-wp.png)

* Click the dropdown arrow in the upper right corner and choose Edit Web Part

![image](/assets/posts/event-registration/edit-properties.png)

* Under "Content Link" copy-paste link to index.html file and under "Appearance" set "Chrome Type" to None

![image](/assets/posts/event-registration/set-link.png)

* Click Install on the Installation Required screen

![image](/assets/posts/event-registration/install-solution.png)

* Click on the 'x' icon to close the dialog

![image](/assets/posts/event-registration/close-dialog.png)

* Click Stop editing icon

![image](/assets/posts/event-registration/stop-editing.png)

* The solution is now ready to go!

## User Views

**Administrators/Organizers View**

![image](/assets/posts/event-registration/view-solution.png)

**Members/Attendees View**

![image](/assets/posts/event-registration/members-view.png)


# User's Guide

## Organizer

* Create an event with New Event button and view what security groups are managers and members with Manage Groups
* View an event's details by clicking the View icon to the left of Title
* Upload a document by clicking the Upload icon under Documents. View and delete options will be present
* Edit, delete, and view an event's roster by clicking the Manage Events icon. View Roster will have a print option
* Type title or date into Search to find a particular event
* To view coures that have already started or ended click the filters button next to Search and click Show inactive events

### Change Members and Managers group

* Navaigate to the "Event-Registration" folder and edit the "eventreg-config.json"
* Enter the name of the new group for either the admin group or the members group

## Attendee

* Type title or date into Search to find a particular event
* View an event's details by clicking the View icon to the left of Title
* Register or unregister by clicking the Registration button
* If regitered for an event, use the Add event calendar button to add it to Outlook