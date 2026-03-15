---
name: check-credits
description: "Check your Solo Works credits balance and get information about purchasing more credits."
user-invocable: true
---

# Check Solo Works Credits

## Steps

1. Call `get_credits_balance` to retrieve the user's balance.

2. Display the balance breakdown:
   - Free credits (from sign-up bonus)
   - Purchased credits
   - Refund credits (from admin refunds)
   - Total available

3. **If balance is low or zero:**
   - "You can purchase more credits at https://soloworks.app/buy"
   - "20 credits cost $3.65 USD ($0.18 per credit)"

4. **If user asks about costs:**
   - Most image editing workflows: 1-2 credits
   - Complex workflows (3D transform): up to 8 credits
   - Call `list_workflows` to see exact costs for each workflow

## Important Note
This balance reflects your web account credits. If you're using an API key, your API credit balance may differ. Visit https://soloworks.app/api-keys for your exact API balance.
