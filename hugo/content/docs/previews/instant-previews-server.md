---
title: Using Instant Previews
aliases:
- "/docs/instant-previews-server"
date: 2019-06-28 12:00:00 +0000
images:
- "/uploads/2018/01/OGimage-01-docs-3x.jpg"
publishdate: 2018-01-15 17:00:00 +0000
authors: []
expirydate: 2030-01-01 04:00:00 +0000
layout: single
menu:
  docs:
    parent: Previews
    weight: 3

---

When using Instant Previews, managing the preview server is done independently from previewing content. To access the preview server controls, navigate to **Settings** > **Previews** > **Instant Previews**.

{{% pretty_screenshot img="/uploads/2019/06/preview-server-controls.png" caption="Preview server controls" %}}

## Server Status

The Instant Preview server may be in one of several states:

| Status | Description |
|---|---|
| Disabled | Instant Previews are disabled. Standard Previews will be used instead. |
| Stopped| The preview server is stopped. |
| Starting| The preview server is starting up. |
| Ready| The preview server is running the Build Command|
| Stopping| The preview server is shutting down.|
| Error| The an error occurred while running the preview server. |
| Hibernating | The server was [shut down due to inactivity](#server-hibernation). |

## Server Actions
Depending on the state of your preview server, several server actions will be available,

| Action | Description |
|---|---|
| Start |  Starts the stopped preview server. |
| Stop |  Stops running preview server. |
| Restart |  Stops the running server and restarts it immediately. |
| Clear Cache & Restart |  Clears the repository and dependency cache before restarting the server. |

## Reading the Server Logs

<video playsinline autoplay muted loop width="100%" controls>
    <source src="/video/starting-preview-server.mp4" type="video/mp4">
  Your browser does not support the video tag.
  </video>

The lifecycle of a preview server contains multiple steps. Each step has a **status indicator**, **name**, and some **logs**. 

{{% warning %}}
Don't panic if you don't see any steps in your server controls. They won't appear until you start the server for the first time.
{{% /warning %}}

Common preview steps include:

| Setup Step | Description |
|---|---|
| Loading Repo Files |  Imports the site repository and mounts it to the container. |
| Installing Dependencies |  Runs the  _Install Dependencies Command_ if it was set. Dependencies will be loaded from cache if it exists. |
| Saving Preview Cache |  Caches the repository and any installed dependencies.  |
| Building Site |  Executes the _Build Command_ to start serving your preview. |


## Server Hibernation

The preview server will automatically shut down if there hasn't been any activity in the CMS for a couple hours, at which point the server will enter the **hibernating** state. When the server is hibernating, any activity inside the CMS will cause it to start up again.

If you manually stop the preview server by clicking the **stop** button, it will not automatically start back up in response to CMS activity, and will instead remain stopped until you manually start it again.