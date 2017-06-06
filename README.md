# kernel-linux-4.7-rc3-80211p
80211p - Linux Kernel based on linux-4.7-rc3 with ath9kdriver and modificaitons to Makefile for AMD64

Basedupon the following
https://github.com/torvalds/linux

https://gist.github.com/lisovy/80dde5a792e774a706a9

Patched Makefile with
"+   wiphy->regulatory_flags |= REGULATORY_CUSTOM_REG;
-   ath_reg_apply_world_flags(wiphy, NL80211_REGDOM_SET_BY_DRIVER, reg);
+   ath_reg_apply_world_flags(wiphy, NL80211_REGDOM_SET_BY_USER, reg);"
