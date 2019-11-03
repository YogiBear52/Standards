# Code Review

One of the most important subjects!

## [Motivation](https://medium.com/palantir/code-review-best-practices-19e02780015f)

- The main way to lean and new things in your team.
- One of the main daily human interaction between your team members.
  - Build Trust
- The obvious - Find bugs, bad design, code smells.
- Many more reasons ------ ADD

## How ?

- Code review should not last more than 30 minutes and will contain fewer than 400 lines of code
  - Plan small and independent tasks in advance
  - Otherwise, it becomes tiring, focus level decrease -> not efficient
  - embrace lightweight rapid Code Reviews
- Use a linter to help you focus on the interesting complicated parts of the C.R
- Before diving into the code
  - Make sure the programmer has done a self C.R
  - Make sure this code has passed a successful pipeline.
  - Make sure you can see all the code Diff (using a GitTool), don't trust the programmer to tell you exactly what part of the code has change. He doesn't really know and will manipulate you.
  - Read the Task. Don't let the programmer tell you.
  - See the result before dipping into the code.
- Code Reviewer should lead the C.R
  - The only one to control the keyboard and mouse.
  - Sit in front of the screen.
- As the code reviewer, **Deeply** understand the code.
  - Think about how would you have solved the problem
  - This is the reason why some prefer a remote code review, so they could quietly understand the code without time pressure or some manipulation of the programmer.
- Make sure all notes are written
  - Later, use them as a reference to make sure all notes have been fixed.
  - In case extracting a big refactor task, write it as a different task and consider do it in another time.
- C.R with small shallow points, is usually a weak C.R. As the reviewer, you can do better.
- Human Interaction
  - Give some compliments. No way the programmer has done only bad things.
  - Teacher-Mode. Teach how to do it right instead of rebuking.
    - Non-Judgmental
  - Don't compromise
    - Even if it is becoming a debate
    - Call another person to reach a verdict
  - Some of the most bad experiences of IT employees is due to harsh Code Reviews.[Link](https://habr.com/en/post/440736/)
- Code Reviewer, Pay Attention! From now on, you are responsible for this code not less than who wrote this code.
  - (?) If a bug occurs, The reviewer will fix it.
- Make a C.R Check-List

## Who should review ?

- (?) Not just senior developers.
  - This is the chance for juniors to get better
  - Not a brand new junior. After some time, let him review some senior's code on small tasks.

## Remote vs Peer C.R

-

## Code Review Check-list

Modify it to be relevant to your project specific requirements.

- Clean Code - Modularity, Single Responsibility, Naming
- Tests
  - Unit Tests
  - Component Tests
  - Integration Tests
  - GUI E2E Tests
- KPI
  - Is the KPI booming?
- Code Design
  - Architectural concerns
- Error handling
- Performance
- UI Responsiveness
- Documentation
- DO YOU APPROVE THIS CODE?
