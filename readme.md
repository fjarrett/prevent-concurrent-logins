<!-- DO NOT EDIT THIS FILE; it is auto-generated from readme.txt -->
# Prevent Concurrent Logins

![Banner](assets/banner-1544x500.png)
Prevents users from staying logged into the same account from multiple places.

**Contributors:** [fjarrett](https://profiles.wordpress.org/fjarrett)  
**Tags:** [login](https://wordpress.org/plugins/tags/login), [users](https://wordpress.org/plugins/tags/users), [membership](https://wordpress.org/plugins/tags/membership), [security](https://wordpress.org/plugins/tags/security), [sessions](https://wordpress.org/plugins/tags/sessions)  
**Requires at least:** 4.1  
**Tested up to:** 4.1  
**Stable tag:** 0.2.0  
**License:** [GPLv2 or later](http://www.gnu.org/licenses/gpl-2.0.html)  

[![Build Status](https://travis-ci.org/fjarrett/prevent-concurrent-logins.png?branch=master)](https://travis-ci.org/fjarrett/prevent-concurrent-logins) 

## Description ##

**Did you find this plugin helpful? Please consider [writing a review](https://wordpress.org/support/view/plugin-reviews/prevent-concurrent-logins).**

* Deters members/subscribers from sharing their accounts with others
* Hardens security by destoying old sessions automatically
* Prompts old sessions to login again if they want to continue
* Ideal for membership sites and web applications

**Important:** If you plan to network-activate this plugin on a multisite network, please install the [Proper Network Activation](https://wordpress.org/plugins/proper-network-activation/) plugin _beforehand_.

**Development of this plugin is done [on GitHub](https://github.com/fjarrett/prevent-concurrent-logins). Pull requests welcome. Please see [issues reported](https://github.com/fjarrett/prevent-concurrent-logins/issues) there before going to the plugin forum.**

## Frequently Asked Questions ##

### Where are the options for this plugin? ###
This plugin does not have a settings page. Simply put, I don't like bloating my plugins with a bunch of options.

Instead, I try to develop functionality using the 80/20 principle so that for 80% of use cases you all you need to do is activate the plugin and it "just works".

For the other 20% of you who want things to behave differently there are hooks available in the plugin so you can customize default behaviors.

### Can I still allow concurrent logins for certain users? ###
Yes, simply add this hook to your theme's `functions.php` file or as an [MU plugin](http://codex.wordpress.org/Must_Use_Plugins):

```php
function pcl_bypass_admins( $user_id ) {
    $user = get_user_by( 'id', absint( $user_id ) );

    if ( ! empty( $user->roles[0] ) && 'administrator' === $user->roles[0] ) {
        return false;
    }

    return true;
}
add_filter( 'pcl_prevent_concurrent_logins', 'pcl_bypass_admins' );
```


## Changelog ##

### 0.2.0 - January 28, 2015 ###
* Destroy old sessions for all users upon activation

Props [fjarrett](https://github.com/fjarrett), [chuckreynolds](https://github.com/chuckreynolds)

### 0.1.1 - January 2, 2015 ###
* Added filter to allow certain users to have concurrent sessions when necessary

Props [fjarrett](https://github.com/fjarrett), [nutsandbolts](https://github.com/nutsandbolts)

### 0.1.0 - December 31, 2014 ###
* Initial release

Props [fjarrett](https://github.com/fjarrett)


