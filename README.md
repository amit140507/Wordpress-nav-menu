# Wordpress-nav-menu

### Add in ``Functions.php``
```
function register_nav_menu( $location, $description ) {
	register_nav_menus( array( $location => $description ) );
}
```
**For Single Menu**
```
function wpb_custom_new_menu_single() {
  register_nav_menu(
  	'primary_menu',__( 'New Primary Menu') 
  );
}
add_action( 'init', 'wpb_custom_new_menu_single' );
```
**For Multiple Menus**
```
function wpb_custom_new_menu() {
  register_nav_menus(
    array(
      'header_menu' => __( 'New Header Menu' ),
      'footer_menu' => __( 'New Footer Menu' )
    )
  );
}
add_action( 'init', 'wpb_custom_new_menu' );
```

### Add in ``Header.php``
```
	<?php 
	wp_nav_menu( 
		array( 
				'menu'                 => '',
		'container'            => 'div',
		'container_class'      => '',
		'container_id'         => '',
		'container_aria_label' => '',
		'menu_class'           => 'menu',
		'menu_id'              => '',
		'echo'                 => true,
		'fallback_cb'          => '',
		'before'               => '',
		'after'                => '',
		'link_before'          => '',
		'link_after'           => '',
		'items_wrap'           => '<ul id="%1$s" class="%2$s">%3$s</ul>',
		'item_spacing'         => 'preserve',
		'depth'                => 0,
		'walker'               => '',
		'theme_location'       => 'primary_menu',

		) 
	); 
	?>
```

## References

[register_nav_menu](https://developer.wordpress.org/reference/functions/register_nav_menu/)

[register_nav_menus](https://developer.wordpress.org/reference/functions/register_nav_menus/)

[wp_nav_menu](https://developer.wordpress.org/reference/functions/wp_nav_menu/)
