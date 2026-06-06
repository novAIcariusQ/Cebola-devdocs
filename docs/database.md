---
title: Database
nav_order: 4
---

# Database
{: .no_toc }

<!-- ## Table Of contents -->
<!-- {: .no_toc .text-delta } -->

<!-- 1. TOC -->
<!-- {:toc} -->

---

## Our database right now vc what we are going for

```mermaid
erDiagram
  direction TB
  %% Our current database
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

  %% What we want
  USER* {
    string id PK
    string subscription_id FK "Can be null"
    date subscription_expire_date "Can be null"
    string email UK
    string password_hash
    string username
    date created_at
    string[] orders_id "Can be NULL"
  }
  USER* ||--o{ SUBSCRIPTION* : Owns
  SUBSCRIPTION* {
    string id PK
    number cost
    string title
    string description
    number length "In days"
  }
  USER* ||--o{ SHOP* : owns
  SHOP* {
    string id PK
    string owner_id FK
    string[] comments FK "Can be null"
    string title
    string description
    image logo
    bool is_active
    bool is_verified
    number created_at
  }
  SHOP* ||--o{ COMMENT* : has
  COMMENT* {
    string id PK
    string user_id FK
    number rate
    number comment_rating
  }
  SHOP* ||--o{ PRODUCT* : has
  PRODUCT* {
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
  PRODUCT* }|--|{ ORDER_ITEM* : "refers to"
  ORDER_ITEM* {
    string id PK
    string product_id FK
    string product_title
    number product_price_at_time
    image product_logo
    number quantity
  }
  SHOP* ||--o{ ORDER* : has
  USER* ||--o{ ORDER* : orders
  ORDER_ITEM* }|--|| ORDER* : "contained in"
  ORDER* {
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

---

## Relationship Syntax

| Value (left) | Value (right) | Meaning |
|--------------|---------------|---------|
| \|o	         | o\|	         | Zero or one |
| \|\|         | \|\|	         | Exactly one |
| }o           | o{	           | Zero or more (no upper limit) |
| }\|          | \|{	         | One or more (no upper limit)  |

Read more about this [here](https://mermaid.js.org/syntax/entityRelationshipDiagram.html#relationship-syntax).
