# php-ubi

NO WORKING NEITHER UBI7 NOT UBI8.
On ubi7 need to find how to start php with httpd both from scl -- httpd not activating php module.
On ubi8 httpd cannot talk to fgci php

Minimal "hello, world" container image based on Red Hat's Universal Base Image (UBI) and PHP.
For more information about UBI, see: https://www.redhat.com/en/blog/introducing-red-hat-universal-base-image

This is a long-running container that returns a "hello, world" HTML page.

You need a Red Hat Developer's account to grab the service account user name and token to download the UBI base images. It is free. :-)
You can also use the unauthenticated registry while it is still available.

Register at https://developers.redhat.com and, while logged in to the Developer's web site, access https://access.redhat.com/terms-based-registry/ to create your registry service account.

On RHEL 7.6+, CentOS, and Fedora, you do:

```
$ sudo podman login -u <your service account name> -p <your service account token>
$ sudo podman build -t php-ubi .
$ sudo podman run --name hello -p 8080:8080 -d localhost/php-ubi
$ curl localhost:8080
<html>
<body>
<?= "Hello world" ?>
</body>
</html>
$ sudo podman stop hello
$ sudo podman rm hello
```

You could use the docker command but I like podman more.
I suppose podman is available from other Linux distros, I don't know about Windows and MacOS.

This container image should work on OpenShift using the default security policy.

