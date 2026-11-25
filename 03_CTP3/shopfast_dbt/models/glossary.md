{% docs gross_revenue %}
**Gross revenue (EUR)**: total amount paid by the customer for an order, VAT included, shipping included, before refunds.
Owner: Head of Sales · Steward: Karim Benali · Status: approved (2026-11-10)
{% enddocs %}

{% docs net_revenue %}
**Net revenue (EUR)**: the money ShopFast keeps from an order once refunds are deducted, without VAT and with shipping fees kept in.
Formula: `round((gross_revenue_eur - refunded_eur) / 1.20, 2)` (VAT 20%).
Example: order 700236, 424.50 paid, no refund -> 353.75. Order 700063, 131.52 paid then refunded -> 0.
The Sales amount with VAT (gross_revenue_eur - refunded_eur) is not net revenue.
Owner: Paul Girard (Head of Finance) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}

{% docs active_customer %}
**Active customer**: a customer account that placed at least one non-cancelled order in the 12 months before the report date.
Rule: `order_date > report_date - 12 months and order_date <= report_date and status <> 'cancelled'`.
Example: on 2026-11-25, account 10328 (last order 2026-07-17, delivered) is active; 1080 active customers in total.
Counted per account, not per person (52 emails are shared by several accounts).
Owner: Paul Girard (Head of Finance) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}

{% docs recently_active_customer %}
**Recently active customer**: a customer account that placed at least one non-cancelled order in the 6 months before the report date.
Rule: `order_date > report_date - 6 months and order_date <= report_date and status <> 'cancelled'`.
Example: on 2026-11-25, account 10328 (last order 2026-07-17) is recently active; 775 in total, all also active customers.
Used by the Sales dashboard and marketing campaigns. Never call it active customer.
Owner: Sara Martin (Head of Sales) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}

{% docs churned_customer %}
**Churned customer**: a customer account that placed at least one non-cancelled order in the past but none in the 12 months before the report date.
Rule: most recent non-cancelled `order_date <= report_date - 12 months`; accounts that never ordered are excluded.
Example: on 2026-11-25, account 10017 (last order 2025-10-16) is churned; 145 in total.
Owner: Sara Martin (Head of Sales) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}

{% docs customer %}
**Customer**: an account registered on ShopFast and identified by one customer_id, whether it has ordered or not.
Rule: `count(distinct customer_id)` in stg_customers.
Example: 1241 raw rows - 8 exact duplicates = 1233 customer accounts, 15 of them never ordered. One person can have several accounts.
Owner: Sara Martin (Head of Sales) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}

{% docs order %}
**Order**: a purchase placed by a customer account at one date on one sales channel, identified by one order_id, whatever its status.
Rule: `count(distinct order_id)` in stg_orders; status in pending, shipped, delivered, cancelled, returned.
Example: 5207 raw rows - 7 duplicates = 5200 orders, 434 of them cancelled.
Owner: Sara Martin (Head of Sales) · Steward: Karim Benali · Status: approved (2026-11-25)
{% enddocs %}
