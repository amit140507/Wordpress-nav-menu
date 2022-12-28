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
## Single Menu
```
function wpb_custom_new_menu_single() {
  register_nav_menu(
  	'primary_menu',__( 'Primary Menu') 
  );
}
add_action( 'init', 'wpb_custom_new_menu_single' );
```
## Multiple Menus
```
function wpb_custom_new_menu() {
  register_nav_menus(
    array(
      'header_menu' => __( 'Header Menu' ),
      'footer_menu' => __( 'Footer Menu' )
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
			'menu'                 => '',
			'container'            => 'nav',
			'container_class'      => 'nav-menu-class',
			'container_id'         => '',
			'container_aria_label' => '',
			'menu_class'           => 'menu',
			'menu_id'              => 'menu-primary-menu',
			'echo'                 => true,
			'fallback_cb'          => 'wp_page_menu',
			'before'               => '',
			'after'                => '',
			'link_before'          => '',
			'link_after'           => '',
			'items_wrap'           => '<ul id="%1$s" class="%2$s">%3$s</ul>',
			'item_spacing'         => 'preserve',
			'depth'                => 0,
			'walker'               => '',
			'theme_location'       => 'my-custom-menu-single',	

		) 
	); 
	?>
```
