# buildah "1" "March 2017" "buildah"

## NAME
Buildah - A command line tool to facilitate working with containers and using them to build images.

## SYNOPSIS
buildah [OPTIONS] COMMAND [ARG...]


## DESCRIPTION
The Buildah package provides a command line tool which can be used to:

    * Create a working container, either from scratch or using an image as a starting point.
    * Mount a working container's root filesystem for manipulation.
    * Unmount a working container's root filesystem.
    * Use the updated contents of a container's root filesystem as a filesystem layer to create a new image.
    * Delete a working container or an image.

This tool needs to be run as the root user.

## OPTIONS

**--debug**

Print debugging information

**--default-mounts-file**

Path to default mounts file (default path: "/usr/share/containers/mounts.conf").  Users can also create an additional conf file, `/etc/containers/mounts.conf`.

The mounts.conf files specify volume mount directories that are automatically mounted inside containers when executing the `buildah run` or `buildah build-using-dockerfile` commands.  Container process can then use this content.  The volume mount content does not get committed to the final image.

Usually these directories are used for passing secrets or credentials required by the package software to access remote package repositories.

For example, a mounts.conf with the line "`/usr/share/rhel/secrets:/run/secrets`", the content of `/usr/share/rhel/secrets` directory is mounted on `/run/secrets` inside the container.  This mountpoint allows Red Hat Enterprise Linux subscriptions from the host to be used within the container.

The format of the mounts.conf is the volume format /SRC:/DEST, one mount per line.
Users can create an `/etc/containers/mounts.conf`, to specify their
own special volumes to mount in the container. Buildah by default reads /usr/share/containers/mounts.conf and the /etc/containers/mounts.conf
if it exists. Specifying the `--default-mounts-file` overrides both `default` mounts files.
Note this is not a volume mount. The content of the volumes is copied into container storage, not
bind mounted directly from the host.

**--help, -h**

Show help

**--registries-conf** *path*

Pathname of the configuration file which specifies which registries should be
consulted when completing image names which do not include a registry or domain
portion.  It is not recommended that this option be used, as the default
behavior of using the system-wide configuration
(*/etc/containers/registries.conf*) is most often preferred.

**--registries-conf-dir** *path*

Pathname of the directory which contains configuration snippets which specify
registries which should be consulted when completing image names which do not
include a registry or domain portion.  It is not recommended that this option
be used, as the default behavior of using the system-wide configuration
(*/etc/containers/registries.d*) is most often preferred.

**--root** **value**

Storage root dir (default: "/var/lib/containers/storage")
Default root dir is configured in /etc/containers/storage.conf

**--runroot** **value**

Storage state dir (default: "/var/run/containers/storage")
Default state dir is configured in /etc/containers/storage.conf

**--storage-driver** **value**

Storage driver.  Default Storage driver is configured in /etc/containers/storage.conf.  Overriding
this option, will drop the storage-opt definitions was well from the storage.conf file.  User must
specify additional options via the `--storage-opt` flag.

**--storage-opt** **value**

Storage driver option, Default Storage driver options are configured in /etc/containers/storage.conf

**--version, -v**

Print the version


## COMMANDS

| Command               | Description                                                                                          |
| --------------------- | ---------------------------------------------------                                                  |
| buildah-add(1)        | Add the contents of a file, URL, or a directory to the container.                                    |
| buildah-bud(1)        | Build an image using instructions from Dockerfiles.                                                  |
| buildah-commit(1)     | Create an image from a working container.                                                            |
| buildah-config(1)     | Update image configuration settings.                                                                 |
| buildah-containers(1) | List the working containers and their base images.                                                   |
| buildah-copy(1)       | Copies the contents of a file, URL, or directory into a container's working directory.               |
| buildah-from(1)       | Creates a new working container, either from scratch or using a specified image as a starting point. |
| buildah-images(1)     | List images in local storage.                                                                        |
| buildah-inspect(1)    | Inspects the configuration of a container or image                                                   |
| buildah-mount(1)      | Mount the working container's root filesystem.                                                       |
| buildah-rm(1)         | Removes one or more working containers.                                                              |
| buildah-rmi(1)        | Removes one or more images.                                                                          |
| buildah-run(1)        | Run a command inside of the container.                                                               |
| buildah-tag(1)        | Add an additional name to a local image.                                                             |
| buildah-umount(1)     | Unmount a working container's root file system.                                                      |
| buildah-version(1)    | Display the Buildah Version Information                                    |
| storage.conf(5) | Syntax of Container Storage configuration file |


## SEE ALSO
podman(1)

## HISTORY
December 2017, Originally compiled by Tom Sweeney <tsweeney@redhat.com>
