---
date: 2021-10-19
layout: post
title: Event Registration
subtitle: 
description: An event registration solution designed for SharePoint 2013/Online environments.
image: /assets/posts/event-registration/view-solution.png
optimized_image: /assets/posts/event-registration/view-solution.png
category: blog
tags:
  - Classic
  - Modern
  - Solution
author: gunjandatta
---

# Event Registration

A tool for organizers to create and manage events in SharePoint Online.

**Original Developers**
_Michael Wilson & Josh Gardner_

# Build

1. Fork the solution and clone it to your machine
2. Install the libraries

```npm i```

3. Link TypeScript

```npm link typescript```

4. Build the Solution

```npm run all```

# Installation and Deployment

1. Go to Site content -> Site Assets where the app shall live
2. Create a new folder and it _must_ be named `Event-Registration`

![image](/assets/posts/event-registration/create-folder.png)

3. Click inside of the folder and upload the following: <br/>

![image](/assets/posts/event-registration/upload-assets.png)

4. Navigate to Site Pages <br/>

![image](/assets/posts/event-registration/site-pages.png)

5. Click New -> Web Part Page
6. Type the name of the page before ".aspx" (era is recommended) and select "Full Page, Vertical" for layout template. <br/>

![image](/assets/posts/event-registration/create-wp.png)

7. Click "Add a Web Part" and set Categories to "Media and Content" and Parts to "Content Editor" <br/>

![image](/assets/posts/event-registration/add-wp.png)

8. Click the dropdown arrow in the upper right corner and choose Edit Web Part <br/>

![image](/assets/posts/event-registration/edit-properties.png)

9. Under "Content Link" copy-paste link to index.html file and under "Appearance" set "Chrome Type" to None <br/>

![image](/assets/posts/event-registration/set-link.png)

10. Click Install on the Installation Required screen <br/>

![image](/assets/posts/event-registration/install-solution.png)

11. Click Refresh after installation is loaded <br/>

![image](/assets/posts/event-registration/refresh-page.png)

12. Click Stop editing if present. 

![image](/assets/posts/event-registration/stop-editing.png)

13. CONGRATULATIONS!!! ERA is now ready to go! It will appear similar to the screen-shots below.

**Administrators/Organizers View**

![image](/assets/posts/event-registration/view-solution.png)

**Members/Attendees View**

![image](/assets/posts/event-registration/members-view.png)


# User's Guide

## Organizer

1. Create an event with New Event button and view what security groups are managers and members with Manage Groups
2. View an event's details by clicking the View icon to the left of Title
3. Upload a document by clicking the Upload icon under Documents. View and delete options will be present
4. Edit, delete, and view an event's roster by clicking the Manage Events icon. View Roster will have a print option
5. Type title or date into Search to find a particular event
6. To view coures that have already started or ended click the filters button next to Search and click Show inactive events

### Change Members and Managers group

1. Navaigate to the "Event-Registration" folder and edit the "eventreg-config.json"
2. Enter the name of the new group for either the admin group or the members group

## Attendee

1. Type title or date into Search to find a particular event
2. View an event's details by clicking the View icon to the left of Title
3. Register or unregister by clicking the Registration button
4. If regitered for an event, use the Add event calendar button to add it to Outlook 
