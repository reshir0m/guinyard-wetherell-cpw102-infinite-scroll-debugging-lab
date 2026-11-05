# Incident Note — INC-204

**Responders:**
Owen W.
Marcus G.
## Investigation log

Record **every debugging step in chronological order as you work**, including unsuccessful attempts and changes you undo. Commit your work as you go. 

For each step, briefly note what you tried and why, what you observed, and what you concluded or decided to try next.

Include relevant inputs, code changes, or output so someone else can follow your investigation. 

Use numbered entries or timestamps. Use Markdown formatting to make it easy to read.

[x] Error 1: Same 3 posts instead of new posts
[x] Error 2: Program keeps looping user endlessly.
[x] Error 3: User inputs anything except "y" or "n"

Processes: 
- run the program
- reproduced user's 1st error
- reproduced user's 2nd error
- reproduced user's 3rd error

- focus on the for loop
- trying rewritten if action to an elif statement
- trying page = page + 1 (works: progresses posts instead of loopng first 3.)

- commented out second page = 0
- uncommented second page = 0

## Resolution

Explain the causes, your repairs, and the evidence that verifies them. Identify
anything still uncertain or unresolved. Make code changes in `feed.py`.

CAUSES:
 1. Same 3 posts on every scroll. The program kept a page numbter to know which posts o show next. When the user would input "y", the steps that move to the next page would get skipped and keep showing page 1.

 2. Never reaching the end. Once all 8 posts were shown, the program had nothing left to load. It didn’t notice, so it kept offering to scroll forever without saying the feed was over.

 3. Bad answers broke it. If you typed something other than yes or no, the program complained but never let you answer again, so it got stuck repeating the complaint. A small typo also made it reject even correct answers the first time.


Repairs

The program now checks whether there are any new posts. If there aren’t, it says “No more posts.” and stops.
When you type something it doesn’t understand, it now asks again instead of getting stuck. It also accepts a capital Y or N, and it ignores extra spaces.
The step that moves to the next page now happens every time you say yes.

Evidence
We tried every situation the assignment describes:

typing “maybe”
typing a capital Y with spaces around it
scrolling all the way to the end
saying no right away
starting with no posts at all