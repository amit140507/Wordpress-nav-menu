# Wordpress-nav-menu

### Add in ``Functions.php``
```
function register_nav_menu( $location, $description ) {
	register_nav_menus( array( $location => $description ) );
}
```
**For Single Menu**
```
function custom_nav_menu_single() {
	register_nav_menu(
		'primary_menu', esc_html__( 'New Primary Menu', 'twentytwentyone' ),
	);
}
add_action( 'init', 'custom_nav_menu_single' );
```
**For Multiple Menus**
```
function custom_nav_menu() {
	register_nav_menus(
		array(
			'header_menu' => esc_html__( 'New Header Menu', 'twentytwentyone' ),
			'footer_menu' => esc_html__( 'New Footer Menu', 'twentytwentyone' ),
		)
	);
}
add_action( 'init', 'custom_nav_menu' );
```

### Add in ``header.php``
```
<?php if ( has_nav_menu( 'header_menu' ) ) : ?>
	<nav aria-label="<?php esc_attr_e( 'New Header Menu', 'twentytwentyone' ); ?>" class="header-navigation">
		<?php 
		wp_nav_menu( 
			array( 
				'menu'                 => '',
				'container'            => false,
				'container_class'      => '',
				'container_id'         => '',
				'container_aria_label' => '',
				'menu_class'           => 'menu',
				'menu_id'              => '',
				'echo'                 => true,
				'fallback_cb'          => false,
				'before'               => '',
				'after'                => '',
				'link_before'          => '',
				'link_after'           => '',
				'item_spacing'         => 'preserve',
				'depth'                => 0,
				'walker'               => '',
				'theme_location'       => 'header_menu',

			) 
		); 
		?>
	</nav><!-- .header-navigation -->
<?php endif; ?>
```

### Add in ``footer.php``
```
<?php if ( has_nav_menu( 'footer_menu' ) ) : ?>
	<nav aria-label="<?php esc_attr_e( 'New Footer Menu', 'twentytwentyone' ); ?>" class="footer-nav">
		<?php 
		wp_nav_menu( 
			array( 
				'menu'                 => '',
				'container'            => false,
				'container_class'      => '',
				'container_id'         => '',
				'container_aria_label' => '',
				'menu_class'           => 'menu',
				'menu_id'              => '',
				'echo'                 => true,
				'fallback_cb'          => false,
				'before'               => '',
				'after'                => '',
				'link_before'          => '',
				'link_after'           => '',
				'item_spacing'         => 'preserve',
				'depth'                => 0,
				'walker'               => '',
				'theme_location'       => 'footer_menu',

			) 
		); 
		?>
	</nav><!-- .footer-nav -->
<?php endif; ?>
```

### Add nav_menu_link_attributes

```
function add_link_atts($atts) {
  $atts['class'] = "nav-link";
  return $atts;nav_menu_link_attributes
}
add_filter( 'nav_menu_link_attributes', 'add_link_atts', 10 , 3 );
```
**For Header Menu Only**
```
function add_specific_menu_location_atts( $atts, $item, $args ) {
	if( $args->theme_location == 'header_menu' ) {
		$atts['class'] = 'nav-link';
	}
	return $atts;
}
add_filter( 'nav_menu_link_attributes', 'add_specific_menu_location_atts', 10, 3 );
```

## References

[register_nav_menu](https://developer.wordpress.org/reference/functions/register_nav_menu/)

[register_nav_menus](https://developer.wordpress.org/reference/functions/register_nav_menus/)

[wp_nav_menu](https://developer.wordpress.org/reference/functions/wp_nav_menu/)
