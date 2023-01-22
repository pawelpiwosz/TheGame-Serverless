# Matt Morgan

The scheduling requirement could be solved with some pretty standard web app stuff. We create events that have a start time and end time and such is reflected in the user experience and validated when voting occurs.

But, the requirement for a five-minute warning makes me rethink that slightly. We definitely need an admin panel by now. In addition to the updates (standard web app stuff), admins can create voting events with a start time, end time, and any additional metadata.

Fifteen minutes prior to the configured time, we trigger a Step Function workflow that sends a reminder to all connected clients (via WebSocket API or AppSync) which are configured for reminders. The workflow will use `Wait` steps to schedule the opening of the voting event (updating status in a DB), the 5-minute warning (again delivered via WebSockets), and the closing of the event (updating status again).

This will allow us to easily check which elections are in progress, set concurrency limits (if desired), and so on as well as introduce error-checking and validation to make sure the results are valid.
