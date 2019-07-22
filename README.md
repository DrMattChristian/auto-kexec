# auto-kexec
Automatically [Kexec](https://wiki.archlinux.org/index.php/Kexec) into latest Linux kernel version.

* Requires that the user executing `auto-kexec` is able to run kexec commands without a password for automation.

Setup in [sudo](https://www.sudo.ws/) via [NOPASSWD tag](https://www.sudo.ws/man/1.8.27/sudoers.man.html#Tag_Spec) for the user.

Example sudoers file, change _USER_ to the correct user running `auto-kexec`:

```
# Allow _USER_ to run systemctl kexec and kexec without a password
_USER_ ALL = NOPASSWD: /usr/bin/systemctl kexec
_USER_ ALL = NOPASSWD: /usr/sbin/kexec
```

---

* Setup `auto-kexec` via [crontab](https://crontab.guru/) as appropriate for your situation and downtime windows.

Example cron job, requires that the `auto-kexec` command can be found in the user's $PATH var:

```
# Auto Kexec into latest kernel version at 2:02 AM every Sunday.
2 2 * * 0 auto-kexec
```

---

* Only actively used and tested on OL and RHEL Linux RPM-based distributions so far.

Other Linux distributions will require changes. Pull requests are welcome and encouraged.
