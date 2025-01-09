![Cover Image](./pdf-images/sko-exercises-cover-image.png)

# Exercises for Mastering Liferay Client Extensions - SKO 2025 Edition

## Table of Contents

* [Exercise 1: TODO](#exercise-1-todo)
* [Exercise 2: Creating and Deploying a Batch Client Extension](#exercise-2-creating-and-deploying-a-batch-client-extension)
* [Exercise 3: TODO](#exercise-3-todo)

## Exercise 1: TODO

## Exercise 2: Creating and Deploying a Batch Client Extension

Here, you'll create a batch client extension to add a Ticket object definition, picklist, and entries in your Liferay instance.

To do this,

1. In computer's file manager, go to `[workspace-root]/exercises/exercise-2`.

1. Rename the `liferay-sample-batch` folder to `liferay-clarity-tickets-batch`.

   **Note**: This client extension project was downloaded from the [Liferay Sample Workspace](https://github.com/liferay/liferay-portal/tree/master/workspaces/liferay-sample-workspace). As a development best practice, use those samples as the starting point for your client extensions.

1. Go into the folder.

1. Delete all files within the `batch` folder.

   This removes the sample client extension data to accommodate the new Ticket object's content.

1. Open the `client-extension.yaml` file using a text editor or IDE.

   You'll define the batch client extension configuration in this file.

1. Replace the file's content with the following code snippet:

   ```json
   assemble:
      - from: batch
        into: batch
   liferay-clarity-ticket-batch:
      name: Liferay Ticket Batch
      oAuthApplicationHeadlessServer: liferay-clarity-ticket-batch-oauth-application-headless-server
      type: batch
   liferay-clarity-ticket-batch-oauth-application-headless-server:
      .serviceAddress: localhost:8080
      .serviceScheme: http
      name: Liferay Ticket Batch OAuth Application Headless Server
      scopes:
         - C_Ticket.everything
         - Liferay.Headless.Admin.List.Type.everything
         - Liferay.Headless.Batch.Engine.everything
         - Liferay.Object.Admin.REST.everything
      type: oAuthApplicationHeadlessServer
   ```

1. Back in the `exercise-2` folder, copy and paste these files into the `liferay-clarity-tickets-batch/batch` folder:

   * 00-list-type-definition.batch-engine-data.json
   * 01-object-definition.batch-engine-data.json
   * 02-object-relationship.batch-engine-data.json
   * 03-object-entry.batch-engine-data.json

   With this, the client extension will create a picklist, the Ticket object definition, a relationship, and some Ticket entries in your Liferay instance upon deployment.

1. Move the `liferay-clarity-tickets-batch` folder to the `[workspace-root]/client-extensions` folder.

   Great! Now that you've fully configured the batch client extension and moved it to the appropriate folder, you'll deploy it into your Liferay environment.

1. Open your terminal.

1. Go to `[workspace-root]/client-extensions/liferay-clarity-tickets-batch`.

1. Run this command to build and deploy the client extension:

   **Blade**:

   ```bash
   blade gw clean deploy
   ```

   **Unix-based systems**:

   ```bash
   ../../gradlew clean deploy
   ```

   **Windows**:

   ```bash
   ..\..\gradlew.bat clean deploy
   ```

1. Verify the command executes successfully in your instance log.

   ```log
   [TODO]
   ```

   Now that you've deployed the batch client extension, let's check the new content.

1. In your Liferay instance, sign in as the Clarity Admin user.

   * Username: `admin@clarityvisionsolutions.com`
   * Password: `learn`

1. Open the *Global Menu* (![Global Menu](./pdf-images/icons/icon-applications-menu.png)), go to the *Control Panel* tab, and click *Objects*.

1. Verify if the `Ticket` object definition is present.

1. In the Global Menu (![Global Menu](./pdf-images/icons/icon-applications-menu.png)), go to the *Control Panel* tab and click *Picklists*.

1. Check if these picklists were created:

   * Ticket
   * Priorities
   * Regions
   * Resolutions
   * Statuses
   * Types

1. In the Global Menu (![Global Menu](./pdf-images/icons/icon-applications-menu.png)), go to the *Control Panel* tab and click *Ticket*.

1. Verify if the Ticket entries were created.

Great! You've successfully created and deployed your first batch client extension.

## Exercise 3: TODO