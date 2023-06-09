# Cloud Native Technologies Workshop

## Description
The Cloud Native Technologies Workshop offers a unique and hands-on learning experience for participants who have completed the Cloud Native learning path. This workshop focuses on creating the backend infrastructure for a photo social network, incorporating key topics in storage, events, database, compute, networking, networking@edge, costs, and authentication. Participants, both teams and individual users, will have the opportunity to apply their knowledge and skills in developing a cloud-native solution.

## Topics
The workshop consists of several sessions, where each session covers multiple interconnected topics that are essential for building the backend of a photo social network. Participants will have the chance to gain practical experience and deepen their understanding of cloud-native technologies within this specific context.

### Foundational Session
Introduction to Cloud Native Backend Development and Photo Upload with Thumbnail Generation
Overview of cloud-native backend architectures and design principles
Understanding the requirements and challenges of building a photo social network backend
Introduction to the topics covered in subsequent sessions
Hands-on Challenge: Participants will implement the functionality to upload photos. Additionally, they will learn how to generate thumbnails for efficient display and user experience.


### Following sessions
After each sessions, new topics and goals will be published here.


Photo Social Network API
========================

This API documentation provides details on the endpoints available for interacting with the Photo Social Network backend. The API allows users to upload, manage, and interact with photos in the social network.




Authentication
--------------

Authentication is required for certain API endpoints. To keep simple the authentication you can use a simple authentication header like the following ones:

Authentication: userId1

Authentication: userId2

Authentication: userId3

Authentication: JohnDoe

Authentication: PeteCocoon

Authentication: EliahSmallearl

For example if you upload a photo with POST /api/photos and you set the authentication header as "Authentication: user_id_1" the photo will be assigned to user_id_1.


Sessions and endpoints
---------
## Session 1: Starting June 1st
### Upload a Photo

-   Endpoint: `POST /api/photos`
-   Description: Upload a photo to the Photo Social Network.
-   Request Body: multipart/form-data
    -   Form field: `image` - The JPG image file to be uploaded.
-   Response:
    -   HTTP 201 CREATED if the photo is successfully uploaded.
    -   Response Body: JSON object containing the generated image ID.
    -   Example:
       { "id": "f1disy1" }

## Session 2: June 22nd
### List Photos

-   Endpoint: `GET /api/photos?userId=userId1`
-   Description: Retrieve a list of photos from the Photo Social Network ordered by upload date
-   Query String Parameter: 
    - Optional: If a userId parameter is set, all the photos of the specified user are returned. Otherwise all the photos you can access will be listed.
-   Response:
    -   HTTP 200 OK.
    -   Response Body: JSON array of photo objects representing the user's photos.
    -   Example:
       
        [
           { "id": "f1disy1", "url": "https://the-url-of-f1disy1.jpg", ... },
           { "id": "sd2jknr", "url": "https://the-url-of-sd2jknr.jpg", ... }
        ]1
 - Note: after session 4 the behaviour of this api will change: 
    - If you call the endpoint without specifying a user ID, the photo wall will be shown. The photowall consists of all your photos (public and private) with public photos of users you follow, sorted by upload date.
    - If you call the endpoint with an user ID, all the PUBLIC user photos of the user will be listed. 
    - If you call the endpoint with the user id that matches the user id of the authentication token, you are listing all of your photos (public or private)

### Get Photo Details

-   Endpoint: `GET /api/photos/{photoId}`
-   Description: Retrieve details of a specific photo.
-   NOTE: 
-   Path Parameter:
    -   `photoId` - The ID of the photo to retrieve.
-   Response:
    -   HTTP 200 OK if the photo exists.
    -   Response Body: JSON object containing the photo details.
    -   Example:
        { "id": "f1disy1", "url": "https://the-url-of-f1disy1.jpg", "size": {"small": "https://the-url-of-f1disy1-SMALL.jpg", "medium": "https://the-url-of-f1disy1-MEDIUM.jpg" }... }
        
 - Note: after session 3 the behaviour of this api will change: 
     - the response body contains the list of comments, the number of likes, the list of user that like the photo
     -   Example:
        { 
            "id": "f1disy1", 
            "url": "https://the-url-of-f1disy1.jpg",
             "size": {"small": "https://the-url-of-f1disy1-SMALL.jpg", "medium": "https://the-url-of-f1disy1-MEDIUM.jpg" },
            "comments": [{"id": "comment_id_123", "content": "this is a comment to your foto",  "userId": "user1", ... }, {"id": "comment_id_123", "content": "this is a comment to your foto",  ... }],
            "likeCount": 123,
            "likes": ["user1", "user2", "user3"]
            ... 
        }

## Session 3: July 6th        
### Comment on a Photo

-   Endpoint: `POST /api/photos/{photoId}/comments`
-   Description: Add a comment to a photo.
-   Path Parameter:
    -   `photoId` - The ID of the photo to comment on.
-   Request Body: JSON object
    -   Example: {"content": "this is a comment to your foto", ... }
-   Response:
    -   HTTP 201 CREATED if the comment is successfully added.
    -   Response Body: 
         {"id": "comment_id_123", "content": "this is a comment to your foto",  ... }

### Like/Unlike a Photo

-   Endpoint: `POST /api/photos/{photoId}/like`
    -   Description: Like a photo.
-   Endpoint: `POST /api/photos/{photoId}/unlike`
    -   Description: unlike a photo.
-   Path Parameter:
    -   `photoId` - The ID of the photo to like/unlike.
-   Response:
    -   HTTP 201 CREATED if the like/unlike is successfully added.
    -   Response Body: 
        {'photoId': 'photoo-id-123'}

## Session 4: July 20th
### Mark a Photo as Private/Public

-   Endpoint: `PATCH /api/photos/{photoId}`
-   Description: Mark a photo as private/public. 
-   Path Parameter:
    -   `photoId` - The ID of the photo to update.
-   Request Body: JSON object
    -   Set photo as private example: `{ "isPrivate": true }`
    -   Set photo as public example: `{ "isPrivate": false }`
-   Response:
    -   HTTP 204 NO_CONTENT

### Delete a Photo

-   Endpoint: `DELETE /api/photos/{photoId}`
-   Description: Delete a photo from the Photo Social Network.
-   Path Parameter:
    -   `photoId` - The ID of the photo to delete.
-   Response:
    -   HTTP 204 NO_CONTENT


### Follow/Unfollow an User
If you follow an user, when you list the photos with the /api/photos endpoint, you will see your photos and the public followed users photos

-   Endpoint: `POST /api/users/{userId}/follow`
    -   To follow a user.
-   Endpoint: `POST /api/users/{userId}/unfollow`
    -   To unfollow a user.
-   Path Parameter:
    -   `userId` - The ID of the user to follow/unfollow.
-   Response:
    -   HTTP 200 OK if the operation is successful.
    -   Response Body: JSON object confirming the follow/unfollow action.

## Session 5: Aug 3rd
Final review and feedback.
