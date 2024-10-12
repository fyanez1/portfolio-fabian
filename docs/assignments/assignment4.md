---
title: Assignment 4 - Backend Design & Implementation
layout: doc
---

**Abstract Data Models** <br><br><br>
![](<../images/Abstract%20data%20model%20(1)-1.png>){:width='500'}

**Design Reflection** <br>

 <p>One of the main changes I made to my concepts was changing the upvoting concept to a 5-star rating system. The reason for this is to allow buyers to have a better sense of how trustworthy a seller is and to better expose when sellers have sold low quality products in the past or items that did not turn out to be as advertised. With upvotes, there is not a way to express negative opinions. Having downvotes as well solves this issue but having a rating out of 5 is more expressive than downvotes since there is a wider range. Other than this concept, all the other concepts were implemented exactly as initially designed in A3. </p>
 <br>
 <p>Another key design choice that had to be made had to do with the claiming concept. Initially, I was planning on mapping items to users to their position in the queue for that item. However, this implementation required too much synchronization between the claiming and selling concepts. Additionally, while it allows for fast retrieval of a user's position in a queue, the removal of a person in the queue is very slow. Instead, I chose to simply have each ClaimDoc to have an array of the users in the queue for that item. Although, this means that getting the position of users is now O(n) instead of O(1), in practice the speed is nearly identical because the size of the queues are extremely small. Therefore, I sacrificed asymptotic time complexity in order to have a simpler backend data structure for the item queues since the runtime, in practice, is nearly identical between the two implementations.</p>
 <br>
 <p>Another key design decision I made was to not include in the backend the logic involving whether or not a user has already rated an item. When a user tries to rate an item out of 5 stars, they must have bought the item and it must also be their first time rating the item, otherwise it would be an update to the rating they already gave. I tried implementing this logic in the backend, but it required too many synchronizations between concepts and added complexity that made the code less readable. On the other hand, this logic will be much easier to implement on the frontend since the data that is necessary to validate whether or not a user can rate an item is at hand and does not require synchronizations like it does with the backend. Therefore, I have chosen to keep the rating concept functions simple and more readable without having to deal with validation. </p>
