### bugs
- setOpen is not defined when clicking Général header. **SOLUTION: make setOpen and open states as global state. Why not using redux instead ? simply the drawer and the header components aren't too nested.       **SOLUTION 02 : i opted for removing the click event from general alltogether as it wasn't good UX to open the menu when clicking on the drawer header


- users
    - infinite reload after removing the authenticatedUser in the people page. **SOLUTION : update authenticated user state in redux store and set it to null
    - updating availability in the menu doesn't update the users list on /home. MUST REFRESH PAGE. **SOLUTION : restore user state from redux store and add it to the useEffect dependency array
    - updating availability in the menu doesn't update the user's availability in the users list on /user. MUST REFRESH PAGE. **SOLUTION : added a useEffect in NewList component with [user] where user was obtained from redux store to update the users state whenever the user availability was changed
    - New created user doesnt show directly on the users list. **SOLUTION : update Users state after receivng an OK response of adding a user

    - Password input's type isn't set to password on people page /user, so the password is visible when typing. **SOLUTION : set input type to password
    - Once a new user is created on the people page, the user is re-directed to the new user details update page on /user/:id. **SOLUTION : remove history.push(`/user/${res.data._id}`)
        - name input is disabled on user details page. **SOLUTION : Cannot update the username because it's unique per user
        - New user is being saved without a name. **SOLUTION : on the api .post("/user") added name: username in the db request, because mongoose was expecting a field named "name" not "username"
        - update a user is not working. **SOLUTION : the LoadingButton has onChange event, i set it to onClick and it's working as expected.

- projects
    - Craches when clicking on a project. **SOLUTION: used findOne instead find in the get("/projects/:id") as it is fetching a unique record (by id). find returns an array and findOne returns an object.
    - New created project doesnt show directly on the projects list, must refresh page. **SOLUTION : update projects state after receivng an OK response of adding a project
    -


- activities
    - when deleting a project in the activity table, i get deleted undefined notification. **SOLUTION: it was activity.project but it should be activity.projectName
    - when deleting a newly created project in the activity table, i get Deleted 500 response error cuz i hit /activity/undefined. as activities state doesn't hold the id of the activity. **SOLUTION: update activities state after receving ok response of adding a new acitivity with the activity id.
    - must refresh page to see changes, when deleting an activity. **SOLUTION: update activities state after receving ok response o fdeleting the activity
    