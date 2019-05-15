# php-ubi

Minimal "hello, world" container image based on Red Hat's Universal Base Image (UBI) and PHP with Apache HTTPd from the Software Collections Library (SCL).

For more information about UBI, see: https://www.redhat.com/en/blog/introducing-red-hat-universal-base-image and https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/building_running_and_managing_containers/index?lb_target=stage#using_red_hat_universal_base_images_standard_minimal_and_runtimes

For more information about SCL, see: https://access.redhat.com/documentation/en-us/red_hat_software_collections/3/

This is a long-running container that returns a "Hello, world!" HTML page. Not very dynamic, I know. ;-) Just make sure you see no '<?php' tags in the generated page.

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
Hello world!
</body>
</html>
$ sudo podman stop hello
$ sudo podman rm hello
```

You could use the docker command but I like podman more.
I suppose podman is available from other Linux distros, I don't know about Windows and MacOS.

This container image should work on OpenShift using the default security policy.

