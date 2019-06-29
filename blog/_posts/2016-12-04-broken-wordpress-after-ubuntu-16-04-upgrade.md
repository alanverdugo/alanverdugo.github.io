---
id: 1806
title: Broken WordPress after Ubuntu 16.04 upgrade
date: 2016-12-04T21:26:48-05:00
author: Alan Verdugo
layout: post
guid: http://www.kippel.net/blog/?p=1806
permalink: /blog/broken-wordpress
#permalink: /?p=1806
categories:
  - Uncategorized
tags:
  - english
  - how-to
  - IT
  - Technical writing
  - webdev
---
<p style="text-align: justify;">
      After some delays, I finally upgraded the server&#8217;s OS to the LTS Ubuntu 16.04. At first I thought that everything went fine, but then I tried to access the blog and it did not work, it only showed a blank page. A very bad omen. Then, when I tried to login into WordPress, this horrible message appeared:
</p>

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false striped:false nums:false wrap:true lang:php decode:true ">` element. * Default 'Log In'. * @param string $message Optional. Message to display in header. Default empty. * @param WP_Error $wp_error Optional. The error to pass. Default empty. */ function login_header( $title = 'Log In', $message = '', $wp_error = '' ) { global $error, $interim_login, $action; // Don't index any of these forms add_action( 'login_head', 'wp_no_robots' ); if ( wp_is_mobile() ) add_action( 'login_head', 'wp_login_viewport_meta' ); if ( empty($wp_error) ) $wp_error = new WP_Error(); // Shake it! $shake_error_codes = array( 'empty_password', 'empty_email', 'invalid_email', 'invalidcombo', 'empty_username', 'invalid_username', 'incorrect_password' ); /** * Filters the error codes array for shaking the login form. * * @since 3.0.0 * * @param array $shake_error_codes Error codes that shake the login form. */ $shake_error_codes = apply_filters( 'shake_error_codes', $shake_error_codes ); if ( $shake_error_codes && $wp_error-&gt;get_error_code() && in_array( $wp_error-&gt;get_error_code(), $shake_error_codes ) ) add_action( 'login_head', 'wp_shake_js', 12 ); $separator = is_rtl() ? ' › ' : ' ‹ '; ?&gt; &gt; get_error_code() ) { ?&gt; site_name; } else { $login_header_url = __( 'https://wordpress.org/' ); $login_header_title = __( 'Powered by WordPress' ); } /** * Filters link URL of the header logo above login form. * * @since 2.1.0 * * @param string $login_header_url Login header logo URL. */ $login_header_url = apply_filters( 'login_headerurl', $login_header_url ); /** * Filters the title attribute of the header logo above login form. * * @since 2.1.0 * * @param string $login_header_title Login header logo title attribute. */ $login_header_title = apply_filters( 'login_headertitle', $login_header_title ); $classes = array( 'login-action-' . $action, 'wp-core-ui' ); if ( wp_is_mobile() ) $classes[] = 'mobile'; if ( is_rtl() ) $classes[] = 'rtl'; if ( $interim_login ) { $classes[] = 'interim-login'; ?&gt;</pre>

<p style="text-align: justify;">
      The message was actually much longer, I am just posting the beginning. If you have suffered with PHP in the past (like me), you will notice that this uninterpreted PHP code. That was my first clue, something was wrong with PHP. I created the infamous test.php page to test if PHP is actually working correctly with Apache. For those of you who haven&#8217;t done this, it basically is a &#8220;hello world&#8221; approach to see if PHP is working correctly. We paste the following code into a file named test.php or pleasework.php or something like that.
</p>

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:php decode:true ">&lt;?php
phpinfo();
?&gt;</pre>

<p style="text-align: justify;">
      Then we move that file to the Apache public directory (/var/www/html, is the default in Ubuntu) and grant it appropriate permissions. Then we go to yourdomain.com/test.php and, if PHP is working, we should see a page with PHP&#8217;s logo and all sorts of information like System, Server API and many more. In my case, I only got another blank page. This meant that something was very wrong with PHP.
</p>

<p style="text-align: justify;">
      So I went into the server via SSH and executed php -v. Turns out I didn&#8217;t even have the php command. How was that possible? Well, turns out PHP5 is no longer the default in Ubuntu 16.04, instead, PHP7 is the default. At some point during the upgrade, PHP was completely uninstalled. So, let&#8217;s install it again:
</p>

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true">apt-get install php</pre>

Then install libapache2-mod-php7.0:

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true">apt install libapache2-mod-php</pre>

Then install php7.0-mbstring:

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true">apt install php7.0-mbstring</pre>

Then install php7.0-mysql:

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true">apt install php-mysql</pre>

Finally, reload Apache&#8217;s configuration:

<pre class="theme:son-of-obsidian font:ubuntu-mono font-size-enable:false toolbar:2 striped:false nums:false lang:sh decode:true">service apache2 reload</pre>

<p style="text-align: justify;">
      Once all that was done, I reloaded the test.php page and it gave me all the information I mentioned before. I also logged in successfully into WordPress. Now I am wondering if I should change the OS to something else than Ubuntu, and if I should change the WordPress theme. There are other problems that need to be solved, but for now WordPress is working as it should and I am happy.
</p>