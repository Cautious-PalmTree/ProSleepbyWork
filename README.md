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

<img width="1413" alt="wireframe" src="https://user-images.githubusercontent.com/47457100/161638132-249e0a29-24dc-410d-8017-cf898d28797e.png">


## Schema 
### Models
#### Get Listing Calls
   | Property      | Type     | Description |
   | ------------- | -------- | ------------|
   | accessToken   | String   |Used to authenticate the request. |
   | clientId      | String   | Used to authenticate the request |
   | apiKey        | String   | Used to authenticate the request |
   | startZGListingID | String   | The starting point for your listings. Used for paging purposes.  |
   | limit | intege   | The number of records in your response.  Max is 100. |
   | 
### Networking
#### List of network requests by screen
   - Home Feed Screen
      - (Read/GET) Query all homes off zillow
```
{
  "status": "success",
  "errors": [],
  "payload": [
    {
      "zgListingId": "5163x5rhuybug",
      "listingAddress": {
        "state": "IN",
        "city": "Santa Claus",
        "zip": "47579",
        "street": "931 W Rudolph Ln",
        "unit": ""
      },
      "listingEmail": "email@example.com",
      "listingName": "",
      "listingPhone": "1234567890",
      "listingStartDate": "2018-12-15T00:04:49.891Z",
      "zillowUrl": "",
      "hotpadsUrl": "",
      "truliaUrl": ""
    }
  ]
}
```

   - Profile Screen
      - (Read/GET) Query homes in user object
      - (Update/PUT) Update user profile image

