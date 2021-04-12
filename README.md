# THE YUMMY

## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
2. [Schema](#Schema)

## Overview
### Description
This application was created to have multiple different recipes items that provide you with the recipes. 

### App Evaluation
- **Category:** Networking 
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer, such as tinder or other similar apps. Functionality wouldn’t be limited to mobile devices, however mobile version could potentially have more features.
- **Story:** Analyzes differrent recipes. 
- **Market:** Any individual could choose to use this app, and to keep it a safe environment.
- **Habit:** This app could be used as often or unoften as the user wanted depending on how deep their social life is, and what exactly they’re looking for.
- **Scope:** First we would start with looking at rercipes, then perhaps this could evolve into a recipe sharing application.

## Product Spec

### 1. User Stories (Required and Optional)

**Required Must-have Stories**

- [x] User log in.
- [x] User can sign up for a new account.
- [x] User can scroll through entrees and clicking on them to view the recipe.
![Alt Text](http://g.recordit.co/UBG1FBZm6b.gif)

**Optional Nice-to-have Stories**

[ ] User can favorite specific entrees.
[ ] User can see trending entree.
[ ] User can create a profile.
[ ] User can comment and like profile.

### 2. Screen Archetypes

* Login 
* Register - User signs up or logs into their account
* Entree Screen - View all the different entrees 
   * Upon selecting entree users matched and recipe screen opens.
* Recipe Screen 
   * Allows user to view recipe of the entree they chose.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Entree Selection
* Profile
* Settings

Optional:
* Recipe Queue
* Discover (Top Choices)

**Flow Navigation** (Screen to Screen)

* Forced Log-in -> Account creation if no log in is available
* Entee Selection (Or Queue if Optional) -> Jumps to Recipes
* Profile -> Text field to be modified.
* Settings -> Toggle settings


## Wireframes
<img src="https://raw.githubusercontent.com/CodePath-Group-Project-TTC/TheYummyRecipeApp/main/Wireframe.jpg" width=600>

### Schema

#### Post

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | createdAt     | DateTime | date when post is created (default field) |
   
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all posts where user is author
         ```swift
         let query = PFQuery(className:"Post")
         query.whereKey("author", equalTo: currentUser)
         query.order(byDescending: "createdAt")
         query.findObjectsInBackground { (posts: [PFObject]?, error: Error?) in
            if let error = error { 
               print(error.localizedDescription)
            } else if let posts = posts {
               print("Successfully retrieved \(posts.count) posts.")
           // TODO: Do something with posts...
            }
         }
         ```
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
      


