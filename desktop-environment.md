# Desktop Environment

![asciicast](https://asciinema.org/a/uB6fukBhwP33fe4Z2MdYIILH8.png)

[https://asciinema.org/a/uB6fukBhwP33fe4Z2MdYIILH8](https://asciinema.org/a/uB6fukBhwP33fe4Z2MdYIILH8)

## Install the epel-release

The epel-release package will configure the epel repository for yum.

> Extra Packages for Enterprise Linux \(or EPEL\) is a Fedora Special Interest Group that creates, maintains, and manages a high quality set of additional packages for Enterprise Linux, including, but not limited to, Red Hat Enterprise Linux \(RHEL\), CentOS and Scientific Linux \(SL\), Oracle Linux \(OL\).

```text
yum install -y epel-release
```

## Use yum groups install the desktop environment

You can use yum groups to easily install a wide range of packages and desktop environments. Run `you grouplist` to see your available options.

```text
yum groupinstall Xfce
```

## Install & enable XRDP

XRDP is the opensource RDP server which is far superior to that of VNC.

```text
yum install -y xrdp
systemctl enable xrdp
systemctl start xrdp
```

## Update firewall

We need to allow RDP port 3389 on the local firewall.

_Note: You may also need to update your firewall rules if you're using a cloud provider \(AWS, Google, Azure, etc..\)_

```text
firewall-cmd --permanent --add-port=3389/tcp
firewall-cmd --reload
```

## Set the default Xclient

```text
echo xfce4-session > ~/.Xclients
```

## Configure local user account

XRDP will use a local user account and password for authentication. Login to your box and issue a `passwd` command to set your users password if you haven't done so already. If you do not know the password simply run it as root such as `sudo passwd <username>`

## Connecting to your desktop

Simply open up your Remote Desktop Connection Client and connect to the host/ip of your new box. Your username and password will be the values we previously set.

