---
date: 2016-10-22
layout: post
title: Minimal Page for SharePoint App Parts
subtitle:
description: Create a blank page in SharePoint.
image:
optimized_image: /assets/img/blog-image.jpg
category: blog
tags:
  - Minimal Page
author: gunjandatta
---

When developing app parts, you want to focus on the main content of the page. Instead of using css and js to hide the ribbon and other parts of the page, I wanted to figure out the minimum required to use JSOM or interact with the REST API. I believe the code example below has the minimum. Please add a comment if this doesn't work for you, or if I missed anything.

#### Updated 10/2020

This updated version will ensure the SP.UI.ModalDialog library works. The library required a reference to the core styling.

```html
<%-- The following 4 lines are ASP.NET directives needed when using SharePoint components --%>
<%@ Page Language="C#" %>
<%@ Register TagPrefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register TagPrefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register TagPrefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>

<!-- Required to be used in an App Part -->
<WebPartPages:AllowFraming runat="server" />

<html>
    <head>
        <title></title>
        <meta name="WebPartPageExpansion" content="full" />

        <!-- Required for the SP.UI.ModalDialog -->
        <link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/Themable/corev15.css">

        <!-- Add your CSS references here (Samples shown below) -->
        <link rel="stylesheet" type="text/css" href="../Content/App.css" />
    </head>
    <body>
        <form runat="server">
            <!-- Required to make posts to SP -->
            <SharePoint:FormDigest runat="server" />

            <!-- SharePoint References -->
            <SharePoint:ScriptLink Name="MicrosoftAjax.js" runat="server" Defer="False" Localizable="false" />
            <SharePoint:ScriptLink Name="sp.core.js" runat="server" Defer="False" Localizable="false" />
            <SharePoint:ScriptLink Name="sp.js" runat="server" Defer="True" Localizable="false" />

            <!-- Add your html here -->

            <!-- Add your JS code here (Samples shown below) -->
            <script type="text/javascript" src="../Scripts/App.js"></script>
        </form>
    </body>
</html>
```

#### Older Template
```html
<%-- The following 4 lines are ASP.NET directives needed when using SharePoint components --%>
<%@ Page Language="C#" %>
<%@ Register TagPrefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register TagPrefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
<%@ Register TagPrefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>

<!-- Required to be used in an App Part -->
<WebPartPages:AllowFraming runat="server" />

<html>
    <head>
        <title></title>
        <meta name="WebPartPageExpansion" content="full" />

        <!-- SP References -->
        <script src="/_layouts/1033/init.js"></script>
        <script src="/_layouts/15/MicrosoftAjax.js"></script>
        <script src="/_layouts/15/sp.core.js"></script>
        <script src="/_layouts/15/sp.runtime.js"></script>
        <script src="/_layouts/15/sp.js"></script>
        <script src="/_layouts/15/sp.init.js"></script>

        <!-- Add your JS libraries here (Samples shown below) -->
        <script type="text/javascript" src="../Scripts/jquery.min.js"></script>
        <script type="text/javascript" src="../Scripts/sprest.min.js"></script>

        <!-- Add your CSS references here (Samples shown below) -->
        <link rel="Stylesheet" type="text/css" href="../Content/App.css" />
    </head>
    <body>
        <form runat="server">
            <!-- Required to make posts to SP -->
            <SharePoint:FormDigest runat="server" />

            <!-- Add your html here -->

            <!-- Add your JS code here (Samples shown below) -->
            <script type="text/javascript" src="../Scripts/App.js"></script>
        </form>
    </body>
</html>
```

Below is the code I would put in the "App.js" file to ensure the SP.ClientContext is available.

```
SP.SOD.executeFunc("sp.js", "SP.ClientContext", function() {
    // Add code here
});

```
