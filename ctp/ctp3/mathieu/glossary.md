{% docs gross_revenue %}
**Gross revenue (EUR)**: total paid by the customer for an order, VAT and shipping included, before refunds.
Owner: Head of Sales, steward: Karim Benali, approved 2026-11-10.
{% enddocs %}

{% docs net_revenue %}
**Net revenue (EUR)**: what ShopFast keeps on an order after refunds, without VAT, shipping included.
Formula: `round((gross_revenue_eur - refunded_eur) / 1.20, 2)`
Example: order 700236, 424.50 paid, no refund = 353.75. Order 700063, 131.52 paid and refunded = 0.
Owner: Paul Girard (Head of Finance), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}

{% docs active_customer %}
**Active customer**: account with at least one non-cancelled order in the 12 months before the report date.
Rule: `order_date > report_date - 12 months and status <> 'cancelled'`
Example: on 2026-11-25, account 10328 (last order 2026-07-17) is active. 1080 in total, counted per account.
Owner: Paul Girard (Head of Finance), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}

{% docs recently_active_customer %}
**Recently active customer**: account with at least one non-cancelled order in the 6 months before the report date.
Rule: `order_date > report_date - 6 months and status <> 'cancelled'`
Example: on 2026-11-25, account 10328 is recently active. 775 in total. Used by the Sales dashboard.
Owner: Sara Martin (Head of Sales), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}

{% docs churned_customer %}
**Churned customer**: account that already had a non-cancelled order, but none in the 12 months before the report date.
Rule: last non-cancelled `order_date <= report_date - 12 months`, accounts with no order are left out.
Example: on 2026-11-25, account 10017 (last order 2025-10-16) is churned. 145 in total.
Owner: Sara Martin (Head of Sales), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}

{% docs customer %}
**Customer**: account registered on ShopFast with one customer_id, with or without orders.
Rule: `count(distinct customer_id)` in stg_customers
Example: 1241 raw rows - 8 duplicates = 1233 accounts, 15 never ordered.
Owner: Sara Martin (Head of Sales), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}

{% docs order %}
**Order**: purchase made by an account on one date and one channel, with one order_id, whatever the status.
Rule: `count(distinct order_id)` in stg_orders
Example: 5207 raw rows - 7 duplicates = 5200 orders, 434 cancelled.
Owner: Sara Martin (Head of Sales), steward: Karim Benali, approved 2026-11-25.
{% enddocs %}
