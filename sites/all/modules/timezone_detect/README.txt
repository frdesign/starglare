================
 INTRODUCTION
================

Original author and current maintainer: 
- Jordan Magnuson <http://drupal.org/user/269983>

Timezone Detect is a lightweight Drupal module that leverages the 
jsTimezoneDetect library for automatic detection and setting of a user's 
timezone via javascript. It can set a user's timezone automatically upon first 
login, and update it on every login if desired.


================
 BENEFITS
================

The setting of user timezones is often fraught with confusion and frustration.

To start with, some users will never update their timezone settings manually, 
even when prompted  to do so at every login; I know this from experience running 
a large website where timezone settings  are an important factor. These same 
users will sometimes complain about confusions caused by incorrect timezone 
settings, though they have not bothered to update their accounts. 

The users who DO follow through on updating their timezone settings are often 
confused about which timezone they inhabit, and which timezone they should 
select--even when provided with a map to click on. The Olson timezone codes 
(e.g. "America/Chicago") are not immediately obvious to everyone, and some users 
are confused when they do not see their particular city listed as an option.

This module mitigates these kinds of issues by setting a sane "best guess" 
default timezone for every user at first login, so that you can:

- Be confident that dates and times are always displayed correctly for all      
  users.
- Carry out time-sensitive cron tasks at the best time for all users (e.g.      
  updating credits overnight, sending out emails in the morning).
- Avoid the common confusions that arise when people attempt to set their       
  timezones manually.


================
 LIMITATIONS
================

This module has all the limitations of javascript timezone detection, and the 
jsTimezoneDetect library: It will not work for users who have javascript 
disabled, it does not do geo-location, and does it care very much about 
historical time zones. For more information on the limitations of 
jsTimezoneDetect, see <http://pellepim.bitbucket.org/jstz>.

All of that being said, jsTimezoneDetect will generally provide good "best 
guess" timezone detection for most users. It accounts for daylight savings time, 
and almost always selects a timezone that can be used equivalently to the user's 
actual timezone, if not actually the same IANA ID.

Javascript timezone detection actually produces more accurate results than 
IP-based geolocation methods in some situations, such as when users are in a 
region that has recently changed timezones, or for users on border areas in low
population regions, where geolocation data may be sparse and inconsistent. 


================
 INSTALLATION
================

This module has no special installation requirements. For general instruction on 
how to install and update Drupal modules see 
<http://drupal.org/getting-started/install-contrib>.


================
 CONFIGURATION
================

This module can be configured by visiting admin/config/regional/timezone_detect.

When using this module it is recommended that you disable the option to "Remind 
users at login if their time zone is not set" in Drupal's regional settings, by 
visiting admin/config/regional/settings and unchecking that option. Otherwise 
users may be asked to set their timezone on first login even when this module 
has already set it via ajax callback. This setting is disabled automatically 
when Timezone Detect is first enabled.


================
 RECOMMENDED
================

More modules for minimizing timezone frustrations:

- Timezone Picker <http://drupal.org/project/timezone_picker>
  Provides a wonderful interactive map for selecting timezones on user account 
  pages. 
