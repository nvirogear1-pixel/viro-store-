# Vyro Gear Storefront

Recovered static storefront source for `https://vyrogearstore.netlify.app/`.

## Structure

- `index.html` contains the static storefront UI.
- `data/catalog.json` contains collections, products, draft Printify mapping fields, and variant link placeholders.
- `images/` contains the recovered product and campaign images served by the existing Netlify deployment.

## Printify Wiring

Each product has legacy fields (`printify_product_id`, `printify_url`, `printify_url_verified`) plus a new structured `printify` object:

```json
{
  "product_id": null,
  "product_url": null,
  "variants": [
    {
      "size": "S",
      "color": "Cream",
      "variant_id": null,
      "url": null
    }
  ]
}
```

Set `printify.product_id`, `printify.product_url`, variant IDs/URLs where available, then set `printify_url_verified` to `true` when the product should show a live Buy on Printify button.
