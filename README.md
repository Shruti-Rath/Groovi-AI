# Groovi-AI
I built a full-stack AI agent platform where a user describes a task in plain English, like 'summarize my unread Gmail every morning and post it to Slack,' and the system creates an autonomous agent for it, with objectives, tools, and a schedule.
I chose Next.js because I needed both the frontend dashboard and the backend API routes in one project, and it made deployment simpler. Server-side routes also kept my API keys off the client. I used React and Tailwind for fast UI building.
For Browserbase, many agent tasks involve interacting with websites that don't have clean APIs. Running a headless browser myself would have meant managing infrastructure, so Browserbase gave me hosted browser sessions I could control from code. That let me focus on the agent logic instead of browser setup.
Each agent stores its schedule, for example 'daily at 10 AM.' A scheduler checks which agents are due and triggers their execution. Each run is saved with a status (success, failed, running) and logs, which feed the live dashboard.
If a run fails, for example because a token expired or an API timed out, the failure is recorded and the user can see the error. For temporary errors I retry a limited number of times before marking the run failed, so one bad run doesn't break the recurring schedule or loop forever.
For the AI part, I ran many different natural-language prompts, including vague and tricky ones, and checked whether the generated configuration was valid and matched what I intended. For the integrations, I tested each one end-to-end with my own accounts, such as sending a Slack message or reading Gmail. For the dashboard and scheduling, I ran short-interval schedules and watched the logs and statuses update correctly. I also added input validation so a bad AI output gets rejected instead of executed. I'd like to add automated tests next.

#Demo Video 
https://grooviai.vercel.app/

