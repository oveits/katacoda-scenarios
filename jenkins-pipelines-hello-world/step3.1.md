Now let us configure Git:

#### Task: Configure Git Plugin

This step configures the Git plugin.

1. In the **Manage Jenkins -> Global Tool Configuration** page, find the section Git -> Git installations -> **Git**.
2. Keep the name **Default** and check the **Install automatically** checkbox.
3. From the **Add Installer** dropdown menue, choose **Run Shell Command**.
4. Copy the command **which git || (apk update && apk upgrade &&  apk add --no-cache git)** into the Command box. This command is valid for the chosen alpine image only and must be adapted for other Linux distributions.
5. In the Tool Home box, enter **/usr/bin/git**.
6. Click **Save**  at the bottom of the page.

Jenkins Pipelines are now ready to use Git.
