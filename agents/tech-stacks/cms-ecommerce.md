# CMS & eCommerce Stack Documentation

## 📝 WordPress
**Nivel:** Avanzado

### Core Concepts
```php
// Custom post type
register_post_type('product', [
  'labels' => ['name' => 'Products'],
  'public' => true,
  'supports' => ['title', 'editor', 'thumbnail'],
]);

// Custom taxonomy
register_taxonomy('product_category', 'product', [
  'label' => 'Categories',
  'hierarchical' => true,
]);

// Custom post meta
$product_price = get_post_meta($post_id, 'price', true);
update_post_meta($post_id, 'price', '99.99');
```

### Theme Development
```php
// functions.php - Game development
// style.css
/*
Theme Name: Custom Theme
Description: Description
Version: 1.0
Author: Your Name
*/

// Template hierarchy
index.php
├── home.php
├── single.php
├── archive.php
├── template-parts/
│   ├── header.php
│   ├── footer.php
│   └── content.php
└── assets/
    ├── css/
    └── js/
```

### Plugin Development
```php
<?php
/**
 * Plugin Name: My Plugin
 * Description: Plugin description
 * Version: 1.0
 */

add_action('init', function() {
  register_post_type('custom', [...]);
});

add_filter('the_content', function($content) {
  return $content . '<!-- Plugin added -->';
});
```

### Database Optimization
```sql
-- Add indexes
ALTER TABLE wp_posts ADD INDEX idx_type_status (post_type, post_status);
ALTER TABLE wp_postmeta ADD INDEX idx_key_value (meta_key, meta_value(100));

-- Optimize queries
SELECT * FROM wp_posts WHERE post_type='post' 
  AND post_status='publish' 
  ORDER BY post_date DESC;
```

### Performance Tips
- Use caching plugins (WP Super Cache)
- Lazy load images
- Minify CSS/JS
- Remove unused plugins
- Optimize database
- Use CDN

### Security
```php
// Sanitize input
$name = sanitize_text_field($_POST['name']);
$html = wp_kses_post($_POST['html']);

// Verify nonce
check_admin_referer('action_nonce');

// Capability check
if (!current_user_can('manage_options')) {
  wp_die('Not authorized');
}

// SQL injection prevention
$wpdb->prepare(
  "SELECT * FROM table WHERE id = %d",
  $id
);
```

## 🛒 PrestaShop
**Nivel:** Avanzado

### Module Development
```php
<?php
class MyModule extends Module {
  public function __construct() {
    $this->name = 'mymodule';
    $this->version = '1.0.0';
    parent::__construct();
  }

  public function install() {
    return parent::install() && 
      $this->registerHook('displayHome');
  }

  public function hookDisplayHome($params) {
    return '<div>Custom content</div>';
  }
}
```

### Template Customization
```smarty
{* Smarty template *}
<div id="products">
  {foreach from=$products item=product}
    <div class="product">
      <h3>{$product.name}</h3>
      <price>{$product.price|string_format:"%.2f"}</price>
    </div>
  {/foreach}
</div>
```

### Database Access
```php
// Using ObjectModel
$customer = new Customer($customer_id);
$customer->firstname = 'John';
$customer->save();

// Raw queries
Db::getInstance()->execute(
  "UPDATE ps_customer SET firstname = 'John' WHERE id_customer = 1"
);

// Select
$results = Db::getInstance()->executeS(
  "SELECT * FROM ps_customer WHERE active = 1"
);
```

### Features
- Multi-currency & multi-language
- Module marketplace
- Theme customization
- Advanced reporting
- Product management
- Order management

## 🛍️ eCommerce Best Practices

### Product Management
```
- Clear descriptions
- High-quality images
- Multiple variants
- Stock management
- SEO optimization
- Category structure
```

### Checkout Optimization
```
- Minimize steps (1-page preferred)
- Guest checkout option
- Multiple payment methods
- Security indicators
- Trust badges
- Clear error messages
```

### Performance
```
- Fast page load (<2s)
- Image optimization
- Lazy loading
- Caching strategy
- CDN for assets
- Database optimization
```

### Security
```
- HTTPS/SSL
- PCI DSS compliance
- Payment gateway security
- Data encryption
- Regular backups
- Security updates
- SQL injection prevention
```

### Analytics & Metrics
```
KPIs:
- Conversion rate
- Average order value
- Customer lifetime value
- Cart abandonment rate
- Return/refund rate
- Traffic sources
```

## 💳 Payment Integration

### Common Gateways
```
- Stripe
- PayPal
- Square
- Worldpay
- 2Checkout
- Local payment methods
```

### Implementation
```javascript
// Stripe example
const stripe = Stripe('pk_test_...');
const elements = stripe.elements();
const cardElement = elements.create('card');

cardElement.mount('#card-element');

form.addEventListener('submit', async (e) => {
  e.preventDefault();
  
  const {token} = await stripe.createToken(cardElement);
  
  // Send to your server
  fetch('/process-payment', {
    method: 'POST',
    body: JSON.stringify({token: token.id, amount})
  });
});
```

---

**Last Updated:** February 13, 2025
