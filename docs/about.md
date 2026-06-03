---
layout: page
title: About
permalink: /about/
---

This is the base Jekyll theme. You can find out more info about customizing your Jekyll theme, as well as basic Jekyll usage documentation at [jekyllrb.com](https://jekyllrb.com/)

You can find the source code for Minima at GitHub:
[jekyll][jekyll-organization] /
[minima](https://github.com/jekyll/minima)

You can find the source code for Jekyll at GitHub:
[jekyll][jekyll-organization] /
[jekyll](https://github.com/jekyll/jekyll)


[jekyll-organization]: https://github.com/jekyll

```mermaid!
erDiagram
  direction TB
  USER {
    string id PK
    string email UK
    string password_hash
    string name
    date created_at
  }
  USER ||--o{ SHOP : owns
  SHOP {
    string id PK
    string owner_id FK
    string title
    string description
    image logo
    bool is_active
    number created_at
  }
  SHOP ||--o{ PRODUCT : has
  PRODUCT {
    string id PK
    string shop_id FK
    string title
    string description
    number price
    image photo_url
    number quantity
    bool is_avalible
    date created_at
  }
  PRODUCT }|--|{ ORDER_ITEM : "refers to"
  ORDER_ITEM {
    string id PK
    string product_id FK
    string product_title
    number product_price_at_time
    image product_logo
    number quantity
  }
  SHOP ||--o{ ORDER : has
  USER ||--o{ ORDER : orders
  ORDER_ITEM }|--|| ORDER : "contained in"
  ORDER {
    string id PK
    string shop_id FK
    string user_id FK "Can be null"
    string[] order_items_ids FK
    string guest_order_id UK "Can be null"
    string status
    string qr_code_data UK "Can be null"
    number total_quantity
    number total_cost
    date created_at
  }
```
