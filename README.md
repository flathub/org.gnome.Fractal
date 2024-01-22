# Fractal

Fractal is a Matrix messaging app for GNOME written in Rust. Its interface is optimized for
collaboration in large groups, such as free software projects, and will fit all screens, big or small.

![screenshot](https://gitlab.gnome.org/World/fractal/raw/main/screenshots/main.png)


[View the full README on the GNOME Gitlab repository](https://gitlab.gnome.org/World/fractal/-/blob/main/README.md)

### Runtime Dependencies

Fractal doesn’t store your **password**, but it stores your **access token** and the **passphrase**
used to encrypt the database and the local cache.

The Fractal Flatpaks use the [Secret **Portal**](https://docs.flatpak.org/en/latest/portal-api-reference.html#gdbus-org.freedesktop.portal.Secret)
to store those secrets. If you are using GNOME this should just work. If you are using a different
desktop environment or are facing issues, make sure `xdg-desktop-portal` is installed along with a
service that provides the [Secret portal backend interface](https://docs.flatpak.org/en/latest/portal-api-reference.html#gdbus-org.freedesktop.impl.portal.Secret),
which is currently only implemented by gnome-keyring.

Any version that is not sandboxed relies on software that implements the [Secret **Service** API](https://www.freedesktop.org/wiki/Specifications/secret-storage-spec/)
to store those secrets. Therefore, you need to have software providing that service on your system,
like gnome-keyring, KeepassXC ([setup guide](https://avaldes.co/2020/01/28/secret-service-keepassxc.html)),
or KWallet (since version 5.97). Once again, if you are using GNOME this should just work.

If you prefer to use software that only implements the Secret Service API while using the Flatpaks,
you need to make sure that no service implementing the Secret portal backend interface is running,
and you need to allow Fractal to access the D-Bus service with this command:

```sh
flatpak override --user --talk-name=org.freedesktop.secrets org.gnome.Fractal
```
