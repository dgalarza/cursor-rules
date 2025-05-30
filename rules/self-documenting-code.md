# Self-Documenting Code

Prefer self-documenting code through clear naming, small functions, and obvious structure rather than explanatory comments. Comments should explain **why**, not **what**.

---

## Guidelines

1. **Use descriptive names** for variables, functions, and classes
2. **Keep functions small** and focused on a single responsibility
3. **Use meaningful constants** instead of magic numbers
4. **Write code that reads like prose**
5. **Only add comments for:**

   * Complex business logic explanations
   * Non-obvious design decisions
   * Warnings about gotchas
   * TODOs with context
   * API/function documentation (when necessary)

---

## Examples

### ❌ BAD – Over-commented, poor naming

```ruby
# Calculate the total price including tax
def calc(p, t)
  # Multiply price by tax rate
  tax = p * t
  # Add tax to price
  total = p + tax
  # Return the total
  return total
end

# Check if user can access
def check(u)
  # Check if user is active
  if u.s == 1  # 1 means active
    # Check if user has premium
    if u.p == true
      return true
    end
  end
  return false
end
```

```javascript
// Process order and apply discounts
function processOrder(order) {
    let total = 0;
    // Loop through items
    for (let item of order.items) {
        // Check if item is on sale
        if (item.salePrice) {
            total += item.salePrice * item.qty; // Use sale price
        } else {
            total += item.price * item.qty; // Use regular price
        }
    }

    // Apply coupon if exists and valid
    if (order.coupon && order.coupon.valid && total > order.coupon.min) {
        // Calculate discount
        let discount = total * order.coupon.percent;
        total = total - discount; // Subtract discount
    }

    return total;
}
```

---

### ✅ GOOD – Clear naming, modular, no need for comments

```ruby
def total_price_with_tax(price, tax_rate)
  price + (price * tax_rate)
end

def can_user_access?(user)
  user.active? && user.premium?
end
```

```javascript
function calculateOrderTotal(order) {
    const subtotal = calculateSubtotal(order.items);
    const discount = calculateCouponDiscount(subtotal, order.coupon);
    return subtotal - discount;
}

function calculateSubtotal(items) {
    return items.reduce((total, item) => {
        const price = item.salePrice || item.price;
        return total + (price * item.quantity);
    }, 0);
}

function calculateCouponDiscount(subtotal, coupon) {
    if (!isCouponValid(coupon, subtotal)) return 0;
    return subtotal * coupon.discountPercentage;
}

function isCouponValid(coupon, subtotal) {
    return coupon?.isValid && subtotal >= coupon.minimumPurchase;
}
```
---
