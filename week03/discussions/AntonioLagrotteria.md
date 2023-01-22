# Antonio Lagrotteria

Based on previous [implementation](https://www.linkedin.com/feed/update/urn:li:activity:7017910225949093888?commentUrn=urn%3Ali%3Acomment%3A%28activity%3A7017910225949093888%2C7017966290929598464%29&replyUrn=urn%3Ali%3Acomment%3A%28activity%3A7017910225949093888%2C7018325221879201792%29&dashCommentUrn=urn%3Ali%3Afsd_comment%3A%287017966290929598464%2Curn%3Ali%3Aactivity%3A7017910225949093888%29&dashReplyUrn=urn%3Ali%3Afsd_comment%3A%287018325221879201792%2Curn%3Ali%3Aactivity%3A7017910225949093888%29)

For frontend part:

Enable websockets via API Gataway and hook it into the frontend.

Modify voting model by adding a start and end timestamp. Make sure existing POST/PUT votings endpoints allow to create/update votings with these new attributes, Frontend will display an active/allowed-to-be-voted voting if current time is in between start and end timestamp. If current timestamp is before start timestamp or after end timestamp, then hide voting or show it opaque as disabled with an inactive label.

For backend:

Modify api gateway endpoint votings to be a step function. Check inputs are correct and if they get modified, make sure where current being step functions flows need to be stopped. Then perform operation(create) with lambda

Create a DynamoDB Stream. Setup an EventBridge Pipe which filters only when a start/ end timestamp gets created. Setup a step function as target with following steps.

1. The first step is a choice state to check if start time is less than 15 minutes. If it is , jump to state 4, otherwise jump to state 
2. State 2 is a wait state that waits until voting start timestamp -15 minutes.
3. The next state is a lambda function which posts a message to the websocket, so that a frontend notification can be provided by the client upon arrival of backend message.
4. Step 4 checks if current time is after end time - 5 minutes. If it is then goes to step 6, otherwise to next 5 one.
5. Last step is a lambda function (or choice) that checks if current user was registered and if so sends message to websocket as earlier.
6. end state.
