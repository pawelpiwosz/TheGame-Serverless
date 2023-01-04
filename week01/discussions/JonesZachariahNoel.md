# Jones Zachariah Noel

Amplify powered for APIs (AppSync - GraphQL), auth, hosting, storage with a SPA app.

Cognito with custom attributes where we can update it whenever the user casts the vote and on login uses the custom attribute value to restrict recasts of votes.

Whenever the user casts the vote, just the vote counters on DynamoDB are increased keeping in mind the votes are anonymous. The confirmation could be from the mutation response - successful or errored.

If there is a need for a real-time board for vote count displays, a subscription which updates whenever any count is increased.
