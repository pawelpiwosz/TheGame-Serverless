# Sam Williams

So I think the biggest thing here is the fact that we now have 'User Clients' and lets call the other one 'agency clients'(they have their own clients)

I would probably keep the existing core data structure

**Idea record**  
pk: clientId  
sk: idea  
... other data about the idea  

and votes would stay the same

**vote record**  
pk: userId  
sk: `${clientId}_${ideaId}`  
pk2: `${clientId}_${ideaId}`  
sk2: userId  

**client details record**  
PK: clientId  
sk: "details"  
...name, email, logo etc.

We could have multiple different records for the client, eg. addresses, preferences, features, admin users

This would handle the clients that sign up with us directly, but also the users through the agency

**Agency-Client Record**  
PK: agencyId  
sk: clientId  
... any other data we need

To get all of the clients for an agency we query where PK == AgencyId. Depending on the request type we can then get all of the client details for each clientId. Using GraphQL might be nice here with the nested resolvers. Main consideration is that if you have a Lambda resolver to get each client details - you'd almost certainly hit your concurrency limit, so stick to VTL resolvers.
