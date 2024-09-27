---
title: Assignment 3 - Convergent Design
layout: doc
---

**SeniorSale** <br>

<p>The main purpose of this app is to centralize the act of selling items at MIT. Typically, this is done through dormspam. However, the large majority of students do not like getting spammed by these emails, especially towards the end of semesters when there are sometimes over five “senior sales” per day. The existence of this app would get rid of dormspam sales and centralize all items being sold on campus on a single platform. Users may look for specific items they need by using the search function of the platform, which is not possible through email since the names of items being sold are typically embedded in powerpoint slides. Additionally, students who have things to sell who do not want to dormspam are more likely to put up their items for sale.  Another benefit of having such a platform is that reading comments under items being sold can prevent buyers from asking questions that have already been answered by the seller. Lastly, having a “claiming” function will standardize the process of claiming items being sold, as this is typically very problematic with sellers having to check email response timestamps to determine which buyer claimed the item first and respond to every subsequent buyer who is not aware of the item having been claimed.
</p><br><br>

**Concepts** <br>
<u>Posting item for sale</u><br>

<ol>
    <li><b>Purpose</b> - post a new item for sale</li>
    <li><b>Operational principle</b> - after posting sale, the item is available for all users</li>
    <li><b>State</b> - name: string, cost: float, description: string, pictures - set of images, contact info: string</li>
    <li><b>Actions</b> - post sale, end sale</li>
</ol>
<u>Commenting</u><br>
<ol>
    <li><b>Purpose</b> - ask questions and make statements about an item for sale</li>
    <li><b>Operational principle</b> - comments under item are shown when an item is chosen by a user</li>
    <li><b>State</b> - text: string</li>
    <li><b>Actions</b> - post comment</li>
</ol>
<u>Claiming item</u><br>
<ol>
    <li><b>Purpose</b> - claim an item for sale so that the seller can see the order in which people claimed an item</li>
    <li><b>Operational principle</b> - buyer may add themselves to the queue and potentially expect to be reached out to by the seller</li>
    <li><b>State</b> - claimed: boolean, queue position: integer</li>
    <li><b>Actions</b> - claim, unclaim</li>
</ol>
<u>Upvoting</u><br>
<ol>
    <li><b>Purpose</b> - Let buyers know which sellers typically sell items exactly as advertised, encourages honest behavior for sellers</li>
    <li><b>Operational principle</b> - buyers may upvote the seller after buying an item</li>
    <li><b>State</b> - number of upvotes: integer</li>
    <li><b>Actions</b> - upvote, remove upvote</li>
</ol>
<u>Authenticating user</u><br>
<ol>
    <li><b>Purpose</b> - authenticate users to map users to people</li>
    <li><b>Operational principle</b> - user enters username and password to authenticate</li>
    <li><b>State</b> - authenticated: boolean</li>
    <li><b>Actions</b> - login, logout</li>
</ol><br><br>

**Dependency Diagram** <br>
![](../images/Dependency%20graph-1.png){:width='500'}
<br><br>

**Wireframes** <br>
![](../images/SeniorSail%20main%20page-1.png){:width='500'}
![](../images/SeniorSale%20item%20page-1.png){:width='500'}
<br><br>

**Design Tradeoffs** <br>
<u>Claim queue</u>

<ol>
    <li><b>Outline</b>: While an item is still up for sale, the seller may see a public queue showing interested buyers in the order in which they added themselves to the queue.</li>
    <li><b>Rationale</b>: Initially, I thought of allowing users to claim an item and block all other users from buying the item. However, there is a potential danger in the buyer not buying the item after claiming it. Having the claim expire is still problematic since other buyers are temporarily blocked. Having a queue allows the seller to contact buyers in order of the queue and choose to move on to the next buyer in the queue if they don’t respond. </li>
</ol>

<u>Downvoting sellers Disallowed</u>

<ol>
    <li><b>Outline</b>: While upvoting is one of the features of the app, downvoting is not implemented.</li>
    <li><b>Rationale</b>: The reason for this is that people with biases towards others can downvote sellers undeservingly. However, buyers may still judge whether or not a seller is trustworthy by seeing the number of items they have sold and the number of upvotes they have received, which is upper bounded by the number of items they have sold since only the buyer may upvote.</li>
</ol>

<u>Sales may only list a single item</u>

<ol>
    <li><b>Outline</b>: Users may not sell items in bulk unless the package deal consists of the same type of item.</li>
    <li><b>Rationale</b>: The reason for this is so that users may search more easily for items that they are looking for. Having different types of items being sold under the same post makes it harder for users to find what they are looking for and ultimately prevent them from buying subsets of the items offered in bulk since this would not be allowed.</li>
</ol>
