# CommandEvents
JS file to allow cross extension function calls

This script allows you to send commands to other extensions also using it.
Access to functions is granted based on a whitelist. You can whitelist a function by adding its path to `eventCmd.whitelist`. For example, lets say you have a function `Model.getContacts();`, to expose this
function you would add `'Model.getContacts'` to `eventCmd.whitelist`.

Lets say that an extension called `UserTagger` has a function like: `Model.getUsertag('Username');`.
If they have added this function to their whitelist, you can call the function as follows:

````javascript
eventCmd.send('UserTagger', ['Model', 'getUsertag'], ['Username'], function(usertag){
    console.log("Received usertag:" usertag);
});
````

The arguments for `eventCmd.send()` are as follows:  
`TargetExtension, Path(Array), Arguments(Array), Success(Callback), Error(Callback)`.
