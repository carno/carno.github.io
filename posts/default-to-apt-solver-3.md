<!--
.. title: Default to APT solver version 3
.. slug: default-to-apt-solver-3
.. date: 2025-09-02 21:03:34 UTC+02:00
.. tags: Debian, TIL
.. category: 
.. link: 
.. description: How to set solver 3 as default for APT
.. type: text
-->

Today I learned, that Debian still does not default to the new solver[^1] - for reasons unknown I
have assumed it's already used out of the box.

As I want to avoid having to think about it or adjust aliases again, I decided to configure it in
APT's configuration[^2]

`/etc/apt/apt.conf.d/90solver`:

```text
binary::apt::APT::Solver "3.0";
```

[^1]: <https://blog.jak-linux.org/2024/05/14/solver3/>
[^2]: <https://discourse.ubuntu.com/t/announcement-3-0-solver-now-default-in-questing-for-apt-get-and-apt-commands/60618>
