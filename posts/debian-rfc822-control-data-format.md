<!--
.. title: Debian RFC822 control data format
.. slug: debian-rfc822-control-data-format
.. date: 2025-01-21 23:34:48 UTC+01:00
.. tags: TIL, Debian
.. category: 
.. link: 
.. description: Debian RFC822 control data format
.. type: text
-->

So, today I learned that Debian has an alternative format for apt sources.

After today's upgrade I noticed a new print in `apt update` output, mentioning `deb822`[^1] style for
storing apt sources.

For my own reference, this is how it looks like for repositories I use on my `siduction`[^2]
installation:

`/etc/apt/sources.list.d/debian.sources`:

```yaml
Components: main contrib non-free non-free-firmware
Enabled: yes
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg
Suites: unstable rc-buggy
Types: deb
URIs: https://deb.debian.org/debian/
```

`/etc/apt/sources.list.d/mozilla.sources`:

```yaml
Components: main
Enabled: yes
Signed-By: /etc/apt/keyrings/packages.mozilla.org.asc
Suites: mozilla
Types: deb
URIs: https://packages.mozilla.org/apt/
```

`/etc/apt/sources.list.d/microsoft-edge.sources`:

```yaml
Components: main
Enabled: yes
Signed-By:  /etc/apt/trusted.gpg.d/microsoft-edge.gpg
Suites: stable
Types: deb
URIs: http://packages.microsoft.com/repos/edge/
```

`/etc/apt/sources.list.d/siduction-extra.sources`:

```yaml
Components: main
Enabled: yes
Signed-By: /usr/share/keyrings/siduction-archive-keyring.gpg
Suites: unstable
Types: deb
URIs: https://packages.siduction.org/extra/
```

`/etc/apt/sources.list.d/siduction-fixes.sources`:

```yaml
Components: main contrib non-free
Enabled: yes
Signed-By: /usr/share/keyrings/siduction-archive-keyring.gpg
Suites: unstable
Types: deb
URIs: https://packages.siduction.org/fixes/
```

`/etc/apt/sources.list.d/syncthing.sources`:

```yaml
Components: stable
Enabled: yes
Signed-By: /usr/local/share/keyrings/syncthing-archive-keyring.gpg
Suites: syncthing
Types: deb
URIs: https://apt.syncthing.net/
```

In the future I should probably adjust to recommendation for keyrings' storage:

> The recommended locations for keyrings are /usr/share/keyrings for keyrings managed by packages,
> and /etc/apt/keyrings for keyrings managed by the system operator.

[^1]: <https://manpages.debian.org/unstable/apt/sources.list.5.en.html#DEB822-STYLE_FORMAT>
[^2]: <https://siduction.org>
