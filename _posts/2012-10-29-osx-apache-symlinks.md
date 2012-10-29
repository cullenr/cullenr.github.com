---
title: OSX Apache Symlinks
layout: post
---

Had a little difficulty finding where to specify the symlink handling for Apache this morning. The config file is located here :

{% highlight bash %}
/private/etc/apache2/users/<username>.conf
{% endhighlight %}

Edit this to look like this if your having problems with OSX not following symlinks on your **DEV** machine.

{% highlight xml %}
<Directory "/Users/cullenr/Sites/">
    Options Indexes MultiViews FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>
{% endhighlight %}

Another thing to remember is that if Apache does not have permission to read a directory above the "source" file/dir in its directory tree then Apache will not show the file in the "target" tree it has been added to even if it can read every dir in this  "target" tree.
