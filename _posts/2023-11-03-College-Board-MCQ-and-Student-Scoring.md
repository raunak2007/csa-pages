---
layout: post
title: Individual Review Ticket
description: Individual Review Ticket
courses: { csa: { week: 11 } }
type: hacks
---
# Scores from Student Scoring:

|Unit|Score|
|--|--|
|1|0.81|
|2|1.00|
|3|0.91|
|4|N/A|
|5|N/A|
|6|1.00|
|7|1.00|
|8|TBA|
|9|TBA|
|10|TBA|

# Plans for College Board Quiz

To prepare for the College Board quiz, I did a practice MCQ test from Barron's AP Computer Science A 2024 book with AP exam level timing and got a 37/40 on the test. All 3 of the questions I got wrong were about recursion. To enhance my recursion MCQ problem-solving skills, I reviewed this [study guide](https://uploads-ssl.webflow.com/605fe570e5454a357d1e1811/60a17ad2619ac7840407ac56_AP-CS-A-Study-Guide-Unit-10.pdf) in order to increase my knowledge of recursion. 

# Review of College Board Quiz

I did fairly great on the College Board quiz and got a 38/40 as indicated by the screenshot below
![image](https://github.com/raunak2007/csa-pages/assets/41299387/422a89bc-805b-4496-89f9-40da06439842)
The only 2 questions I got wrong were Question 39 and Question 40, which were both on recursion. 

For Question 39, I put answer choice C. However, that is incorrect the value of recur(6) is 12. However, this call was made within another recursive call and is not the final return value. The correct answer is answer choice D. This is because the call recur(27) returns the value of recur(recur(9)) since 27 is greater than 10. The call recur(9) returns 18, since 9 is less than or equal to 10. Therefore, recur(recur(9)) is recur(18). The call recur(18) returns recur(recur(6)) since 18 is greater than 10. The call recur(6) returns 12, since 6 is less than or equal to 10. Therefore, recur(recur(6)) is recur(12). The call recur(12) returns recur(recur(4)) since 12 is greater than 10. The call recur(4) returns 8, since 4 is less than or equal to 10. Therefore, recur(recur(4)) is recur(8). The call recur(8) returns 16, since 8 is less than or equal to 10.  Therefore, recur(27)returns the value of 16. 

For Question 40, I put answer choice A. However, that is incorrect because his would be the output if the System.out.println(temp); line was before the recursive call to whatsItDo(temp); When the recursive call whatsItDo(temp); is executed, the current sequence of statements are paused. The correct answer is answer choice C. This is because the call whatsItDo(“WATCH”) assigns to temp a substring of “WATCH” starting at 0 and ending at 4 – 1 or 3, which is “WATC”. Next the call whatsItDo(“WATC”) is made. The call whatsItDo(“WATC”), sets its local temp to “WAT” and calls whatsItDo(“WAT”). The call whatsItDo(“WAT”), sets its local temp to “WA” and calls whatsItDo(“WA”). The call whatsItDo(“WA”), sets its local temp to “W” and calls whatsItDo(“W”). The call whatsItDo(“W”) reaches the base case and doesn’t do anything since the length of “W” is 1. Then we need to finish the call to whatsItDo(“WA”), which prints the value of its local temp, “W”.  Then we need to finish the call to whatsItDo(“WAT”), which prints the value of its local temp, “WA”. Then we need to finish the call to whatsItDo(“WATC”), which prints the value of its local temp, “WAT”. Then we need to finish the call to whatsItDo(“WATCH”), which prints the value of its local temp, “WATC”. Therefore, the recursive calls are complete.

# My Contribution to Team Project
I had the most commits out of all of my group members by far, and my commits were roughly evenly spread out over a 3 week period from Oct 15 to Nov 2, with a peak occuring 2 weeks before N@tM.
![image](https://github.com/raunak2007/csa-pages/assets/41299387/aed0f61d-4e7a-4d58-90b0-e52d36bb477f)
![image](https://github.com/raunak2007/csa-pages/assets/41299387/79f68b1a-d812-4410-bbcf-c87b66fe19cb)

Commit History for this trimester:
![image](https://github.com/raunak2007/csa-pages/assets/41299387/6fe0b7d5-0d1c-427b-8903-193fbb65996b)

Code Review:
My main contribution to the team project was the login feature, which can be found [here](https://github.com/A-REEL/a-reelB/blob/gh-pages/login.js)

Time Box:

![image](https://github.com/raunak2007/csa-pages/assets/41299387/ec4eda11-63a3-4282-9702-91cd2d065ee9)

# Reflection

In summary, I am grateful to have the experience of taking AP Computer Science A at Del Norte High School, and I'm especially grateful for all the learning opportunities I've had this trimester. From learning about JWT verification to having a breakfast with my team, I have had a variety of fun experiences this trimester. I've also learned a lot from my other classmates and have built upon their experiences in Computer Science A. I'll look forward to using my experience this trimester in my CS internships and and even later on in college.



