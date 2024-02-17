Imagine an ecommerce website which can sell an unlimited number of units of 5 different
items without any storage cost.
In every webpage, a single product, called primary, is displayed together with its price. The
user can add a number of units of this product to the cart. After the product has been added
to the cart, two products, called secondary, are recommended. When displaying the
secondary products, the price is hidden. Furthermore, the products are recommended in two
slots, one above the other, thus providing more importance to the product displayed in the
slot above. If the user clicks on a secondary product, a new tab on the browser is opened
and, in the loaded webpage, the clicked product is displayed as primary together with its
price. At the end of the visit over the ecommerce website, the user buys the products added
to the cart.
We assume that the user has the following behavior:
● she/he buys a number of units of the primary product if the price of a single unit is
under the user’ reservation price; in other words, the users’ reservation price is not
over the cumulative price of the multiple units, but only over the single unit;
● once the primary product has been bought, the user clicks on a secondary product
with a probability depending on the primary product except when the secondary
product has been already displayed as primary in the past, in this case the click
probability is zero (thus, in practice, excluding the case in which a product is
displayed as primary more than once --- as a result the number of webpages visited
by the user is finite);
● when observing the secondary products, the user initially observes the first slot and,
after having observed that slot, observes the second slot. Assume that the probability
with which the first slot is observed is 1, while the probability with which the second
slot is observed is lambda < 1. The value of lambda is assumed to be known in all
the three project proposals.
Notice that the probability of a click on a secondary product depends on:
● the purchase probability of the primary product,
● the probability to observe the slot in which the secondary product is displayed, and
the click probability of the secondary product conditioned to the purchase of the
primary.

Consider the scenario in which:
● for every primary product, the pair and the order of the secondary products to display
is fixed by the business unit and cannot be controlled,
● the price of every primary product is fixed and this price is equal, for simplicity, to the
margin,
● there are 5 advertising campaigns, one per product, and, by a click to a specific ad,
the user lands on the corresponding primary product.
The ecommerce website has a budget cap B to spend to advertise its products. For
simplicity, assume that the automatic bidding feature provided by the platforms is used and
therefore no bidding optimization needs to be performed. The change of the budget spent on
the campaign for the product Pi changes the expected value of the corresponding 𝛼_i, and
therefore the number of users landing on the webpage in which product Pi is primary. For
every campaign, you can imagine a maximum expected value of 𝛼_i (say 𝛼_i_bar)
corresponding to the case in which the budget allocated on that campaign is infinite.
Therefore, for every campaign, the expected value of 𝛼_i will range from 0 to 𝛼_i_bar,
depending on the actual budget allocated to that campaign.
Step 1: Environment. Develop the simulator by Python. In doing so, imagine a motivating
application and choose the probability distributions associated with every random variable.
Assume that there are 2 binary features that define 3 different users’ classes. The users’
classes potentially distinguish for the 𝛼 ratio functions. More precisely, every class is
characterized by a profile of 𝛼 functions, one per campaign. Given a campaign, the three
classes may have different 𝛼 functions.
Step 2: Optimization algorithm. Formally state the optimization problem where the objective
function is the profit, defined as the difference between the expected margin and the spent in
advertising. Design an exact, dynamic-programming algorithm to optimize the function when
all the parameters are known. Notice that the value per click provided by an advertising
campaign is the expected margin from landing to the corresponding product. Furthermore, in
the dynamic-programming algorithm, you can find the best way to spend the budget, for
every feasible value of the budget, neglecting that the budget spent is to subtract from the
objective function. Thus, you can use the standard dynamic-programming algorithm. After
you have filled the entire dynamic-programming table, you can subtract the corresponding
budget spent from the value of every cell of the last row and then look for the best allocation
maximizing the difference between expected value and budget spent. Deveop the algorithm
by Python.
Step 3: Optimization with uncertain 𝛼 functions. Focus on the situation in which the binary
features cannot be observed and therefore data are aggregated. Design bandit algorithms
(combining GP with UCB and TS) to face the case in which the alpha functions are
unknown. Deveop the algorithms by Python and evaluate their performance when applied to
your simulator.
Step 4: Optimization with uncertain 𝛼 functions and number of items sold. Do the same of
Step 3 to the case in which also the number of items sold per product are uncertain. Deveop
the algorithms by Python and evaluate their performance when applied to your simulator.
Step 5: Optimization with uncertain graph weights. Do the same as Step 3 in the case the
only uncertain parameters are the graph weights. Develop the algorithms by Python and
evaluate their performance when applied to your simulator.
Step 6: Non-stationary demand curve. Now assume that the demand curves could be
subjected to some abrupt changes. Use a UCB-like approach with a change detection
algorithm to face this situation and show whether it works better or worse than using a
sliding-window UCB-like algorithm. Develop the algorithms by Python and evaluate their
performance when applied to your simulator.
Step 7: Context generation. Do the same of Step 4 when the features can be observed by
the ecommerce website. For simplicity, activate the context-generation algorithms every 2
weeks. With multiple contexts, each single context can be optimized independently of the
others. Notice that the split is performed simultaneously over all the campaigns. For
instance, if you decide to split over a binary feature, then the split will be performed over all
the 5 campaigns simultaneously. This is done to simplify the number of possible splits one
can deal with. Once you splitted in multiple contexts, every context can be used to target the
ads at best. More precisely, features can be used as target information of the campaigns,
thus leading to replicate the campaigns. For instance, if the algorithms split according to a
binary feature generating two contexts, then the 5 campaigns are replicated for every single
context, say C1 and C2. Reasonably, C1 and C2 will be characterized by different 𝛼
functions. In this case, the budget optimization problem includes 10 campaigns. This is
equivalent to say that we need to decide whether to assign more budget, e.g., to the
campaign of P1 for C1 rather than to the campaign of P1 for C2. Develop the algorithms by
Python and evaluate their performance when applied to your simulator.
For the Steps 3-7, in the algorithm evaluation, report:
● the average regret and reward computed over a significant number of runs,
● their standard deviation,
● when theoretical bounds are available, also report the ratio between the empiric
regret and the upper bound
