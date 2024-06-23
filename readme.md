# Wordpress deployment using GitHub Actions and rsync

This repository provides configuration for GitHub Actions to deploy a WordPress website to a production server via rsync.

To make it work, you need to set up variables in your repository settings:

Settings -> Security -> Secrets and variables -> Actions

`SSH_HOST`
`SSH_PORT`
`SSH_USERNAME`
`SSH_KEY`

You can generate an SSH key in your hosting provider's control panel.

Set up the `DEPLOY_FOLDER` variable to match your server's `public_html` directory.

After the initial deployment, install WordPress and copy your `wp-config.php` to the *DEPLOY_FOLDER*`/private/shared` directory. Then, uncomment the "Share wp-config file" action in `main.yml` file. From now on, your `wp-config.php` will be shared between versions.

Place any files that you don't want to copy to production inside a `.rsyncignore` file.

Finally, configure your website document root to *DEPLOY_FOLDER*`/public`. You can also do this in your hosting provider's control panel.