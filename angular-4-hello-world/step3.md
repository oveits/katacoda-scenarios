Once the plugins have been installed, you can configure how pipelines uses Git and Maven to download and build a hello world application.

#### Task: Configure Maven Plugin

This step configures the Maven plugin.

1. Once again, select **Manage Jenkins**.
2. Select **Global Tool Configuration**.
3. At the bottom, there is a button called **Maven installations...**. Click it.
4. Choose the name **M3**.
5. Click the **Install automatically** checkbox and keep the option **Install from Apache** with version 3.5.0.
6. Click **Apply**  at the bottom of the page.

#### Task: Configure Git Plugin

This step configures the Git plugin.

1. In the **Manage Jenkins** page, find the section Git -> Git installations -> **Git**.
2. Keep the name **Default** and check the **Install automatically** checkbox.
3. From the **Add Installer** dropdown menue, choose **Run Shell Command**.
4. Copy the command **which git || (apk update && apk upgrade &&  apk add --no-cache git)** into the Command box. This command is valid for the chosen alpine image only and must be adapted for other Linux distributions.
5. In the Tool Home box, enter **/usr/bin/git**.
6. Click **Save**  at the bottom of the page.

Jenkins Pipelines are now ready to use Git and Maven.
