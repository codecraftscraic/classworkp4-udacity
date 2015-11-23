## Design Choices
# How/Why Sessions and Speakers are implemented
I implemented session classes in this manner, because a session may have multiple speakers, and the speaker may speak several times at a conference. You'll notice that I followed the conventions of conference that were already laid out, so, DRY. No need to re-invent the wheel.

I added the repeated sessionToAttend to profile for wishlist, so that the user is able to add multiple sessions to their wishlists, which contains a parent-child relationship similar to the conference and sessions relationship.

Although much of the work could be abstracted out into different objects, for simplicity I only abstracted where I deemed necessary.

One thing I would like to note for the technical implementation is that when I implemented speakers as a part of the session, I wanted to make sure that a session could have multiple speakers, as in a panel, live coding session, etc., but the properties/fields for the definition wouldn't let me have repeated and required in the speaker field, I chose to implement repeated on the back end, and required on the front end. That way, the database could handle multiple speakers, but the front end would make sure that there was at least one speaker for each session.

# Describe Additional Query Types
I chose unfinished conferences and sessions to give conference organizers the ability to check when they have need to either finish filling out their conference, or for them to be able to reach out to session presenters to be sure that they have all of the information they need for conference programs.

In addition, this would enable users to take a look at the conferences and sessions that aren't quite filled out, and be able to decide if they are still worthy of registering for. 

# Reason and Solution for the problem with provided query
- Reason: The problem with the query in front of us is that you are only allowed to have one inequality parameter and this query provides two.

- Solution: Not the ideal solution, but you can do a couple things. You could run each query separately, then compare the results of the two queries, returning where the query results meet the requirements. Or, (and the better option, in my opinion) you can run the one of the queries as a subquery. It's faster, returns what you need, and avoids having two inequalities in the main query.


App Engine application for the Udacity training course.

## Products
- [App Engine][1]

## Language
- [Python][2]

## APIs
- [Google Cloud Endpoints][3]

## Setup Instructions
- Install Google App Engine SDK for Python
- Clone this repository

Optional Steps
1. Update the value of `application` in `app.yaml` to the app ID you
   have registered in the App Engine admin console and would like to use to host
   your instance of this sample.
1. Update the values at the top of `settings.py` to
   reflect the respective client IDs you have registered in the
   [Developer Console][4].
1. Update the value of CLIENT_ID in `static/js/app.js` to the Web client ID
1. (Optional) Mark the configuration files as unchanged as follows:
   `$ git update-index --assume-unchanged app.yaml settings.py static/js/app.js`

Required Step
1. Run the app with the devserver using `dev_appserver.py DIR`, and ensure it's running by visiting
   your local server's address (by default [localhost:8080][5].)

Optional Steps Continued
1. Generate your client library(ies) with [the endpoints tool][6].
1. Deploy your application.


[1]: https://developers.google.com/appengine
[2]: http://python.org
[3]: https://developers.google.com/appengine/docs/python/endpoints/
[4]: https://console.developers.google.com/
[5]: https://localhost:8080/
[6]: https://developers.google.com/appengine/docs/python/endpoints/endpoints_tool
