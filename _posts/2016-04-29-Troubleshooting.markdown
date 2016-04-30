---
layout: post
title:  "Troubleshooting"
date:   2016-04-29 19:47:41
categories: others
---
### Analyze and Understand the Problem
This is a very important step to resolving any problems. I often see people skipping this step by jump right into conclusions, and get caught in a loop with wild guesses.

As the title speaks for itself you need to ANALYZE and UNDERSTAND the problem.

#### _Analyze:_
A clear description of the problem.

- What it is? What is it NOT? What things do have the problem?
- Where is it? Where is it NOT?
- When is it occurring? When is it NOT?
- What is the impact on the business?

#### _Understand:_
Understand how can the problem occur, and list down what could be wrong. Ask others who also know about the problem (Communicate!).

### collecting information on the problem
It's time for some discovery! In this step you should be searching, reproducing the problem, and gathering as much information as you can. The more information you have the easier you can identify the root cause of the issue.

#### _Search:_
If its a known problem, try googling the symptoms or the error (if there is any), see if you can find anything that might help you with the issue. If it's an application you are troubleshooting, start by looking into the logs. Basically use all the channels you can to collect information.

#### _Reproduce the problem:_
Try it yourself, see how is it that you get the problem. Pay good attention to details. Try to map your search findings to what you are experiencing and take note.

### Getting to the root cause:
As you collect enough information you should move forward and try to locate the problem. There are three steps you can follow to narrow down the problem and get to the root cause.

#### _Possible causes:_
Based on the information you've gathered you can list down what you think could be causing the problem.

Question what's happening.

- What's the differences between the places where the problem is and is not happening?
- Any recent deployments?
- Any environment changes?
- If there are changes, how could they cause the problem?

You might end up with a big list of possible causes. You can *devide and conquer*.

_Divide the problem into a few separate parts, and examine one by one:_

you divide the problems into subproblems, and test each side separately to locate the side with the problem.

![Divide and conquer](https://s3.amazonaws.com/ka-cs-algorithms/divide_conquer_1_step.png "Divide and conquer")

_You can use fishbone diagrams too. This specially works well when you are doing cause and effect analysis:_

![fishbone diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Ishikawa_Fishbone_Diagram.svg/2000px-Ishikawa_Fishbone_Diagram.svg.png "fishbone diagram")

Repeat until you isolate the problem. There may be times where you feel you need more information and in my opinion that is fine and it happens. Just go back a step and get more information.

#### _Analyze your findings:_

Some questions to ask yourself here:

- How do these causes explain why the problem is happening?
- What are the assumptions?

If you have a few causes here think about which one is the most probable.

#### _Confirm the cause:_
Get some additional information to confirm the root cause. Try to get your causes proven/checked. See if it's possible to isolate the causes and confirming them.

### Trying fixes:

As you identify the culprit, you should go on and make a change to fix that. But, don't just make changes and forget about it! You will need to continue and monitor the situation. Some questions to keep in mind:

- Has the fix been successful?
- Do the symptoms still appear?

You will have to repeat the steps above if problem still persists or your changes introduce new problems. It's good to refer back to your step on identifying the problem. Refer to the diagrams you drew, or your note and check if you missed any thing. This time you have more information, and you already know what you tried did not resolve the problem so you can cross something off your list of possible causes.

### Go further:

As you get the issue solved, don't just stop there! Think about how you can imporve the app, process, or whatever it is you were fixed. _"Leave it a little better than you found it."_

