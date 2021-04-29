# Installation

We assume a Debian system, adapt to your OS when required (file path, commands, etc).

This probe requires bash.

Add to your probe collector:

```
# /etc/munin/plugin-conf.d/42-php.conf
[php_fpm_num]
env.phpfpmcmd php-fpm7
```

Copy in your plugin directory, and link to enable.

```bash
MUNIN_SHARE_PLUGIN=/usr/share/munin/plugins
MUNIN_ETC_PLUGIN=/etc/munin/plugins

wget \
	-c https://raw.githubusercontent.com/LupusMichaelis/munin-php/trunk/php_ \
	-O $MUNIN_SHARE_PLUGIN/php_

ln -snf $MUNIN_SHARE_PLUGIN/php_ $MUNIN_ETC_PLUGIN/php_fpm_num
chmod 0555 $MUNIN_SHARE_PLUGIN/php_

systemctl restart munin-node
```
