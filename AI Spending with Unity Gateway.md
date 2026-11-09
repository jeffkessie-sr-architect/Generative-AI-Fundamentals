# AI Spending with Unity Gateway


# 1. The Challenge

A team is running an AI application that charges based on token consumption.

As usage increases, costs can grow quickly. The organization wants to:

Prevent excessive API requests.
Control AI spending.
Set spending limits for individual users or teams.
Prevent one team from consuming the entire AI budget.

The solution is to use Unity Gateway rate limits and budgets.

# 2. Unity Gateway Capabilities

Unity Gateway provides two important capabilities:

## A. Rate Limits

Rate limits control how frequently users or applications can make requests.

They help prevent excessive usage and protect services from being overwhelmed.

Example:

A team is allowed to make 100 requests per minute.

If the team exceeds that limit, additional requests can be restricted.

## B. Budgets

Budgets control how much money can be spent on AI usage.

They can be configured for different scopes, such as:

Individual users.
Teams.
Workspaces.

When a spending threshold is reached, budgets can trigger blocking to prevent further consumption.

Example:

A team has a monthly AI budget of $500.

When its spending reaches the configured threshold, Unity Gateway can block additional usage.


# 3. Workflow


       +---------------------------+
       |       AI Application      |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |       Unity Gateway       |
       +-------------+-------------+
                     |
              +------+------+
              |             |
              v             v
     +----------------+  +----------------+
     |  Rate Limits   |  |    Budgets     |
     |                |  |                |
     | Control number |  | Control AI    |
     | of requests    |  | spending      |
     +-------+--------+  +-------+--------+
             |                   |
             v                   v
     +----------------+  +----------------+
     | Check request  |  | Check estimated|
     | frequency      |  | spending       |
     +-------+--------+  +-------+--------+
             |                   |
             +---------+---------+
                       |
                       v
             +-------------------+
             |  Within limits?   |
             +---------+---------+
                       |
                 +-----+-----+
                 |           |
                YES          NO
                 |           |
                 v           v
          +-------------+  +-------------+
          | Allow usage |  | Block usage |
          +-------------+  +-------------+

# 4. Are Budgets an Instant Hard Stop?

Budgets operate using near-real-time spending estimates.

This means:

Spending information may take time to update.
The budget threshold may not be detected immediately.
Additional usage may occur before blocking takes effect.
Budgets should not be treated as guaranteed instant spending caps.

For example:

A team has a $500 budget.

Its estimated spending reaches $500, but the latest usage information may not yet reflect every request.

Therefore, the system might allow additional consumption before the threshold is detected and blocking takes effect.

Key point: Budgets help control spending, but they do not guarantee an instantaneous hard spending limit.

# 5. Why Use Both Capabilities?

Using rate limits and budgets together provides better control.

**Rate limits prevent excessive request activity.**
**Budgets help prevent uncontrolled AI spending.**
**Both help organizations manage usage across teams and workspaces.**


# 6. Conclusion

Unity Gateway provides two important cost and usage controls:

Rate limits: Control how frequently users or teams can make requests.
Budgets: Control estimated AI spending per user, team, or workspace and can block usage when a threshold is reached.

Remember that budgets use near-real-time estimates, so they are not guaranteed instant hard stops.