# Update an App with Continuous Availability

## Goal

Use routes to perform an application upgrade with blue/green deployment.

Approximate time: 25 minutes

## Exercises

### Push a simple PHP app

In the CLI, make sure you are targeting your correct installation org and development space.

In the CLI, verify that your Cloud Foundry includes a PHP buildpack (use cf help if needed).

create a php-app-<your initials and a random number> directory. The name must be unique when deploying the app.

Inside this directory create a single file "index.php"

```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>Hello world</title>
    </head>
    <body>
          <p>Hello world<?php echo " version 1"; ?></p>
    </body>
</html>
```



cf push your simple PHP application. Use your browser to verify that while you stage (push) the app, your application is down.

Use App Manager or the CLI to view the route for your simple PHP application. We want this route to always contain a working application, even though we will upgrade the application's version.

### Create a second version of your application

Copy your PHP application directory, appending an "a" to the directory name. This will be the name of the version 2 application.

In this new directory, modify the index.php file to contain "version 2" instead of "version 1".

cf push this version 2 application, naming it the same as the new directory name. Verify that you now have two different applications with two different routes.

In a browser, access your version 2 application on its unique route.

### Perform upgrade of app from v1 to v2.
Let's assume your application is now ready to upgrade. Add a route on your version 2 app to point to the route on the version 1 app.  Refresh your browser a few times using the original route. Notice that both versions are sometimes displayed.

Remove the route to the version 1 application. Now on the original route, you should only see version 2 of the application. The end users never experienced any downtime.
