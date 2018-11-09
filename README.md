# SparkPlugs
Database functions:

createUserDoc: when new user is authenticated, creates user doc

createUserData: when new user doc is created, creates private and public data placeholders in it

deleteSpot: when users/[userid]/listings/[spotid] is deleted, delete the real spot id from spots/
  
linkSpot: create dummy spot in users/[userid]/listings/ when it is created in spots/
  
moveToHistory: when spots/[spotid] is updated to change fullfilled = true, populate users/<userid>/history with spot info


Implications:

When adding parking spot: document to spots/ when creating spot; payload must contain:
                 
                 typename string description;
                 
                 typename string location;
                 
                 typename number price;
                 
                 typename latlng geoloc;
                 
                 typename boolean fulfilled = false;
                 
                 typename string userid = request.auth.uid;
                 
When deleting spot: delete only document inside users/[userid]/listings/
  
When transaction parking spot transaction is successful: admin privileges update spots/[spotid] to change fulfilled to true
  
When user creates authentic account, should automatically set up basic user doc stuff

