# ProSleepbyWork


## Table of Contents
1. [Overview](#Overview)
1. [Product Spec](#Product-Spec)
1. [Wireframes](#Wireframes)
1. [Schema](#Schema)

## Overview
### Description
Shows real estate available but narrowed down from company location radius. The goal is to be able to show comparisons of different housing metros and jobs available.

### App Evaluation
- **Category:** Business/Lifestyle
- **Mobile:** This app would be primarily developed for mobile but would perhaps be just as viable on a computer. Functionality wouldn't be limited to mobile devices.
- **Story:** Analyzes realestate available around company office locations
- **Market:** Users that are open to relocating for work and looking for best ROI for their career choice. This will streamline the process of looking for jobs and living in large metro areas.
- **Habit:** This app can be used when users are looking for a new job, new real estate to buy or rent or want to compare cost of living difference choices. This has an ability to thrive with the phenomenon of "Zillow Addiction" 
- **Scope:** First we would build a zillow type application but with searching company locations and looking at real estate within the radius of the chosen location. Could build future functionality focused torwards real estate or job postings.

## Product Spec
### 1. User Stories (Required and Optional)

**Required Must-have Stories**

* App shows a map similar to zillow
* User chooses which company location they need to find a place to live.
* Stream list of real estate available
* Settings (Accesibility, Notification, General, etc.)

**Optional Nice-to-have Stories**

* Comparison by metro calculator
* Profile pages of top companys and their metros
* Sign in & Registration 
* 

### 2. Screen Archetypes

* Login 
* Register - User signs up or logs into their account
   * Not required to signin 
   * ...
* Map Screen - Main Search Page
* Stream List Page 
* Company List Page
* Settings Screen
   * Lets people change language, and app notification settings.

### 3. Navigation

**Tab Navigation** (Tab to Screen)

* Map & Search Page
* Company list page
* Stream Real Estate Page
* Settings

Optional:
* Comparison calculator
* Profile/Registration page 

**Flow Navigation** (Screen to Screen)
* Registration & LoginPage -> Option to login or skip
* Map and search page -> pull up list
* Profile -> Text field to be modified. 
* Settings -> Toggle settings 

## Wireframes

<img src="https://i.imgur.com/lYHn37F.jpg" height=200>

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FYORzodKjNz1Du4f5Ovknjq%2FUntitled%3Fnode-id%3D0%253A1" allowfullscreen></iframe>


## Schema 
### Models
#### Post

   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | objectId      | String   | unique id for the user post (default field) |
   | author        | Pointer to User| image author |
   | image         | File     | image that user posts |
   | caption       | String   | image caption by author |
   | commentsCount | Number   | number of comments that has been posted to an image |
   | likesCount    | Number   | number of likes for the post |
   | createdAt     | DateTime | date when post is created (default field) |
   | updatedAt     | DateTime | date when post is last updated (default field) |
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
      - (Create/POST) Create a new like on a post
      - (Delete) Delete existing like
      - (Create/POST) Create a new comment on a post
      - (Delete) Delete existing comment
   - Create Post Screen
      - (Create/POST) Create a new post object
   - Profile Screen
      - (Read/GET) Query logged in user object
      - (Update/PUT) Update user profile image
#### [OPTIONAL:] Existing API Endpoints
##### An API Of Ice And Fire
- Base URL - [http://www.anapioficeandfire.com/api](http://www.anapioficeandfire.com/api)

   HTTP Verb | Endpoint | Description
   ----------|----------|------------
    `GET`    | /characters | get all characters
    `GET`    | /characters/?name=name | return specific character by name
    `GET`    | /houses   | get all houses
    `GET`    | /houses/?name=name | return specific house by name

##### Game of Thrones API
- Base URL - [https://api.got.show/api](https://api.got.show/api)

   HTTP Verb | Endpoint | Description
   ----------|----------|------------
    `GET`    | /cities | gets all cities
    `GET`    | /cities/byId/:id | gets specific city by :id
    `GET`    | /continents | gets all continents
    `GET`    | /continents/byId/:id | gets specific continent by :id
    `GET`    | /regions | gets all regions
    `GET`    | /regions/byId/:id | gets specific region by :id
    `GET`    | /characters/paths/:name | gets a character's path with a given name
