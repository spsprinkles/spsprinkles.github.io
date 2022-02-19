---
date: 2022-02-05
layout: post
title: Solutions WebPart
subtitle: 
description: A webpart that loads various solutions from a configuration file.
image: /assets/solutions/solutions-wp.png
optimized_image: /assets/solutions/solutions-wp.png
category: solutions
tags:
  - Classic
  - Modern
  - Solutions
  - Teams
author: gunjandatta
---

This modern webpart will load a solution from a configuration file. This will allow for classic solutions to be easily managed and approved by the tenant or site collection administrator, based on the scope of the deployment. Users will require a minimum of read access to the solution assets and webpart configuration file. Solutions can be added/upgraded dynamically by updating the configuration file and associated solution assets.

All solutions will follow the initialization used by our solutions where a global DOM variable is made available containing a render method. The render method will be passed the webpart's DOM element and page context for interaction with the REST API.

**Original Developer**
_Gunjan Datta_

## Solution Code

The solution is designed to be used as is or further customized. [Click here](https://github.com/spsprinkles/solutions-wp) to access the code repository. To create your own the instance of the solution, follow the steps below.

1. [Fork the solution](https://github.com/spsprinkles/solutions-wp) and clone it to your machine
2. Install the libraries: `npm i`
3. Build the Solution: `npm run package`

# Installation and Deployment

## Upload Package

* Go to app catalog
* Click the upload button

![image](/assets/posts/solutions-wp/upload-package.png)

* Upload the [package file](https://github.com/spsprinkles/solutions-wp/raw/main/dist/solutions-wp.sppkg)

![image](/assets/posts/solutions-wp/select-file.png)

* Select the `Make this solution available...` checkbox if you want to deploy the solution to teams
* Click the deploy button

![image](/assets/posts/solutions-wp/deploy-solution.png)

_Optional_

* Select the file
* Click on `Sync to Teams` to make the solution available in Teams

![image](/assets/posts/solutions-wp/deploy-to-teams.png)

## Create a Page

* Navigate to the target site
* Click on the `Pages` or `Site Pages` library
* Create a site page

![image](/assets/posts/solutions-wp/create-page.png)

* Name the page
* Add the webpart

![image](/assets/posts/solutions-wp/add-webpart.png)

* Publish the page

![image](/assets/posts/solutions-wp/publish-page.png)

### Solutions Configuration

Now that the solution has deployed and added to a page, we will now walk through the initial configuration of it.

#### Create the Configuration File

The first error is valid, since we haven't set the configuration url property of the webpart. Without this, the webpart will not know what solutions are available. For this solution we will use the `ClientSideAssets` library in the absolute root site collection.

_Note - This property can be automatically defaulted, but will require you to fork it and set it manually._

![image](/assets/posts/solutions-wp/configuration-url-not-set.png)

* Access the target library to store the configuration file
  * We will use the library located in the absolute root site collection `/ClientSideAssets`

![image](/assets/posts/solutions-wp/client-side-assets.png)

* Create a folder called `solutions`

![image](/assets/posts/solutions-wp/create-folder.png)

* Create a file called `config.json` and populate it with the available solutions

```json
{
  "sourceUrl": "/clientsideassets/solutions",
  "solutions": [
    {
      "global": "SCAdmin",
      "name": "Site Collection Admin Tool",
      "url": "sc-admin.min.js"
    }
  ]
}
```

##### Configuration File

| Property | Description |
| --- | --- |
| sourceUrl | The relative url to the folder containing the solutions. |
| solutions | An array of solutions. |
| global | The global DOM variable to reference the solution. |
| name | The name of the solution. |
| url | The url to the solution file found within the source folder. |

Each solution must create a global DOM variable, referenced by the `global` property name, and contain a `render` method. The `render` method will have 2 properties passed to it:

* domElement - The webpart's main element
* context - The page context

#### Upload Solutions

For this solution, we will use the `Site Collection Administration Tool` available from our solutions. Download the [sc-admin.min.js](https://github.com/spsprinkles/sc-admin/raw/main/dist/sc-admin.min.js) solution file and upload it to the same folder containing the configuration file.

![image](/assets/posts/solutions-wp/upload-solutions.png)

#### Set the Configuration File URL

* Refresh the page containing the `Solutions Webpart` created in the earlier steps
* Edit the page and webpart
* Set the URL to the configuration file we just created: `/clientsideassets/solutions/config.json`

![image](/assets/posts/solutions-wp/set-configuration-url.png)

* Edit the page
* Edit the webpart
* Set the url to the configuration file
* Click the `Apply` button to load the available solutions

![image](/assets/posts/solutions-wp/load-solutions.png)

* Select a solution from the dropdown
* Click the `Apply` button to load the solution

![image](/assets/posts/solutions-wp/select-solution.png)

* Click `Republish` to save the changes

![image](/assets/posts/solutions-wp/save-changes.png)

### View the Solution

![image](/assets/solutions/solutions-wp.png)