# Update an App with Continuous Availability

## Goal

Use Cloud Foundry routes to perform an application upgrade with the blue/green deployment strategy.

Approximate time: 25 minutes

## Prerequisites

1. Using `cf buildpacks`, verify that your Cloud Foundry foundation includes a PHP buildpack. If you have a lot of buildpacks you might want to run `cf buildpacks | grep php` (assuming you're using gitbash or a linux command line).

## Exercises

### Push a simple PHP app

1. Using `cf target`, make sure you are targeting your correct org and space for the labs.
2. Clone this repository to your local disk (of you haven't already), and cd into the lab4 directory directory.
3. Inside this directory, verify that there is a file `index.php` that has the contents:
```php
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Hello world</title>
    </head>
    <body>
          <p>Hello world <?php echo "version 1"; ?></p>
    </body>
</html>
```
> :warning: Note: In Windows apps, when saving the `index.php` file, make sure the file type is set to "\*.\* All files". Otherwise, by default, Windows will append `.txt` to the file name, which will cause the deployment to fail when detecting which buildpack to use.
There will also be a manifest.yml file.
4. At the command prompt, change your working directory to the `lab4` directory:
```shell
cd lab4
```
5. Using `cf push`, deploy your simple PHP application with `-blue` in its name. Using your browser, verify that while you deploy the app, your application is down.
```shell
cf push php-app-<YOUR_ID>-blue
```
5. Once the `-blue` version of your app is deployed, using `cf map-route` (remember cf help is your friend), map a new route to it without the `-blue` appended. This is the *production route* for your app. (Tip: You can find your foundation's DOMAIN using `cf routes`, it's your apps domain.)
```shell
cf map-route php-app-<YOUR_ID>-blue <DOMAIN> --hostname php-app-<YOUR_ID>
```
7. Using Apps Manager or `cf route`, view the production route for your application. This route should always map to a working application, even while you upgrade the application.

### Update your application and deploy this updated version

1. Modify the `index.php` file to contain "version 2" instead of "version 1".
2. Using `cf push`, deploy this version 2 application, appending `-green` this time:
```shell
cf push php-app-<YOUR_ID>-green
```
3. Using `cf apps` and `cf app`, validate that you now have two different app deployments with two different routes.
4. Using your browser, validate your `-green` app deployment on its unique route.

### Perform upgrade of app from v1 to v2.

Once you have validated your updated app, you are ready to upgrade.

1. Using `cf map-route`, first map the production route to the `-green` app deployment.
2. Using your browser, reload the production route a few times. Notice that sometimes version 1 is returned, and sometimes version 2.
3. Using `cf unmap-route`, unmap the production route from the `-blue` app deployment.
4. Using your browser, reload the production route a few times. You should only see version 2 of the application.

You have successfully upgraded your application! Note that at no time during the upgrade was your application unavailable.
