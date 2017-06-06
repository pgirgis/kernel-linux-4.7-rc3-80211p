# kernel-linux-4.7-rc3-80211p
80211p - Linux Kernel based on linux-4.7-rc3 with ath9kdriver and modificaitons to Makefile for AMD64

Basedupon the following
https://github.com/torvalds/linux

https://gist.github.com/lisovy/80dde5a792e774a706a9

Patched with
From e21f502fbc3858c3ed3cc8ee97f64f41214e43d7 Mon Sep 17 00:00:00 2001
From: A Raghavendra Rao <arrao@cdac.in>
Date: Mon, 21 Dec 2015 11:29:29 +0530
Subject: [PATCH 01/17] Regd changes

- Removed REGULATORY_STRICT_REG flag to support all ath9k cards
- Modified NL80211_REGDOM_SET_BY_DRIVER to NL80211_REGDOM_SET_BY_USER
  This flags will enforce the user space regulatory domain to be used

Signed-off-by: A Raghavendra Rao <arrao@cdac.in>

---
 drivers/net/wireless/ath/regd.c |    5 ++---
 1 file changed, 2 insertions(+), 3 deletions(-)

diff --git a/drivers/net/wireless/ath/regd.c b/drivers/net/wireless/ath/regd.c
index b1e4171..dec6ec7 100644
--- a/drivers/net/wireless/ath/regd.c
+++ b/drivers/net/wireless/ath/regd.c
@@ -633,8 +633,7 @@ ath_regd_init_wiphy(struct ath_regulatory *reg,
    const struct ieee80211_regdomain *regd;

    wiphy->reg_notifier = reg_notifier;
-   wiphy->regulatory_flags |= REGULATORY_STRICT_REG |
-                  REGULATORY_CUSTOM_REG;
+   wiphy->regulatory_flags |= REGULATORY_CUSTOM_REG;

    if (ath_is_world_regd(reg)) {
        /*
@@ -654,7 +653,7 @@ ath_regd_init_wiphy(struct ath_regulatory *reg,

    wiphy_apply_custom_regulatory(wiphy, regd);
    ath_reg_apply_radar_flags(wiphy);
-   ath_reg_apply_world_flags(wiphy, NL80211_REGDOM_SET_BY_DRIVER, reg);
+   ath_reg_apply_world_flags(wiphy, NL80211_REGDOM_SET_BY_USER, reg);
    return 0;
 }

-- 
1.7.9.5
