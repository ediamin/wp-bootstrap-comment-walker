wp-bootstrap-comment-walker
======================

**A custom WordPress comment walker class to implement the [Bootstrap 3 Media object](http://getbootstrap.com/components/#media) in wordpress comment list.**

Installation and Usage
------------
Place **class-wp-bootstrap-comment-walker.php** in your WordPress theme folder `/wp-content/your-theme/`

Open your WordPress themes **comments.php** file  `/wp-content/your-theme/comments.php` and in this file you should see a snippet like this:

```php
<ol class="comment-list">
    <?php
        wp_list_comments( array(
            'style'       => 'ol',
            'short_ping'  => true,
            'avatar_size' => 56,
        ) );
    ?>
</ol><!-- .comment-list -->
```
The above snippet copied from the comments.php of twentyfifteen theme. Now replace the similar code in your `comments.php` with this following code:
```php
<ul class="list-unstyled">
    <?php
        // Register Custom Comment Walker
        require_once('class-wp-bootstrap-comment-walker.php');

        wp_list_comments( array(
            'style'         => 'ul',
            'short_ping'    => true,
            'avatar_size'   => '64',
            'walker'        => new Bootstrap_Comment_Walker(),
        ) );
    ?>
</ul><!-- .comment-list -->
```