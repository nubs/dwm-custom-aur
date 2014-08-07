# dwm-custom-aur
An [AUR] package build for my personal [dwm] configuration.

## Building
You can of course build this package using [makepkg], but the recommended way
of building this package is using [Docker].  This can be done like so:

```bash
docker build --tag dwm-custom-aur .
docker run --rm --volume "$(pwd):/package" dwm-custom-aur
```

Alternatively, using [Fig]:

```bash
fig run build
```

This will start create a docker image tagged as dwm-custom-aur and build the
package inside the container.  As a result you should get the built package in
your current directory.

[AUR]: https://aur.archlinux.org/
[dwm]: http://dwm.suckless.org/
[makepkg]: https://wiki.archlinux.org/index.php/Makepkg
[Docker]: https://www.docker.com/
[Fig]: http://www.fig.sh/
