# Wordpress-nav-menu


https://developer.wordpress.org/reference/functions/register_nav_menu/

https://developer.wordpress.org/reference/functions/wp_nav_menu/

https://developer.wordpress.org/reference/functions/register_nav_menus/

## Functions.php
```
function register_nav_menu( $location, $description ) {
	register_nav_menus( array( $location => $description ) );
}
```
```
function wpb_custom_new_menu_single() {
  register_nav_menu(
  	'my-custom-menu-single',__( 'My Custom Menu Single') 
  );
}
add_action( 'init', 'wpb_custom_new_menu_single' );


function wpb_custom_new_menu() {
  register_nav_menus(
    array(
      'my-custom-menu' => __( 'My Custom Menu' ),
      'extra-menu' => __( 'Extra Menu' )
    )
  );
}
add_action( 'init', 'wpb_custom_new_menu' );

```

## Header.php
```
<?php 
	wp_nav_menu( 
		array( 
			'theme_location' => 'my-custom-menu',
			'container_class'     => 'nav-menu-class',
			'menu_class'          => 'menu',
			'menu_id'       => 'menu-primary-menu',
			'container' => 'nav',
			'fallback_cb'          => 'wp_page_menu',
		) 
	); 
	?>
```
