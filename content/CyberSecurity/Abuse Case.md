## Abuse case #1

## A user misuses the shopping cart by adding a large quantity of products without the intent to purchase

Reserving stock when a user adds an item to their shopping cart is convenient for the user but reduces buying opportunities for other users. Consider the following security controls to mitigate the risk:

- Reserve stock when a user starts the checkout process, rather than when they add items to their cart. Supplement by communicating low-stock conditions to the user. For example, add a notification to the product page or open a popup once an item has been added to the cart to indicate that there are only “X” units left in stock.
- Limit the number of items allowed in the shopping cart. The limit can be a heuristic based on popularity. For example, put a lower limit on hot selling-items allowed in the cart.
- Implement timers on items added to the cart, or to the entire cart. Once the time limit expires, release reserved stock back into the pool of available items.
- Support oversubscription through a feature to compensate users whose orders couldn’t be fulfilled (e.g., guaranteed delivery on their next order, a discount or voucher).
- Monitor and release. If the stock inventory level is within a predefined threshold, raise an alert. Customer support should have a way to check on related carts, reservation times, and reservation patterns. They should be able to terminate a suspicious reservation with the use of standardized customer communication or protocols to help manage customer expectations.

## Abuse case #2

## Denial-of-service attack with anonymous accounts

Attackers can take advantage of the anonymity of the shopping cart to attack the system by repeatedly opening a browser, creating a new cart, and reserving a large quantity of items. The monitor-and-release control explained above can help. Also consider heuristic controls:

- Implement tiered trust. Assign additional privileges to registered accounts, and fewer to anonymous accounts. For example, change the reservation limit and holding time based on registered/anonymous status.
- Use “likelihood to action” to prioritize inventory holding. You can measure and use information such as referral headers, mouse movements (hot spot tracking), UA, PC resolution, IP range, geo data, and so on to determine a ”likelihood to action” analysis (based on historic sales data), which can help you decide whether to reserve that user’s stock.

## Abuse case #3

## Automated denial of service attacks using botnet or testing tools

Attackers may use botnets or testing tools to create shopping carts and reserve products periodically. This can exhaust your inventory with constant holdings. Mitigate this risk with the following controls:

- Use a [no-CAPTCHA reCAPTCHA control](https://googleonlinesecurity.blogspot.com/2014/12/are-you-robot-introducing-no-captcha.html) to prevent automated attacks.
- Subscribe to IP exclude feeds and use IP “threat intelligence” to screen out automated botnet attacks.
- Limit browser sessions with “suspicious” item reservation requests. These include reserving many of a single item, adding many items to a cart quickly (e.g., adding more than one item a second to the cart), or continuous periodical reservation requests from the same IP.

Misuse and abuse cases can be an effective tool to drive security requirements that protect business features or processes. By designing countermeasures against misuse or abuse cases, you can identify proper security controls. Since these controls are usually interwoven with business features, you need to assess them carefully for their business impact. Apply common security principles and best practices, such as defense-in-depth, monitoring, detection, and prevention, to help define proper security requirements and design appropriate security controls.


[Threat Modeling](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html) is a set of techniques for anticipating what can go wrong, and ensuring we do something about each identified possible scenario. Taking each item on the list of "what are we going to do about it" and writing an abuse case may help your engineering teams process the output.

The project [OWASP Open SAMM](https://owasp.org/www-project-samm/) proposes the following approach in the _Stream B_ of the Security Practice _Requirements Driven Testing_ for the Maturity level 2: