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

Authentication is required for certain API endpoints. Please refer to the API documentation for specific authentication requirements.

Endpoints
---------

### Upload a Photo

-   Endpoint: `POST /api/photos`
-   Description: Upload a photo to the Photo Social Network.
-   Request Body: multipart/form-data
    -   Form field: `image` - The JPG image file to be uploaded.
-   Response:
    -   HTTP 200 OK if the photo is successfully uploaded.
    -   Response Body: JSON object containing the generated image ID.
    -   Example:
       { "id": "f1disy1" }

### List Photos

-   Endpoint: `GET /api/photos`
-   Description: Retrieve a list of photos from the Photo Social Network.
-   Response:
    -   HTTP 200 OK.
    -   Response Body: JSON array of photo objects representing the user's photos.
    -   Example:
        [
           { "id": "f1disy1", "url": "https://the url of f1disy1.jpg" },
           { "id": "sd2jknr", "url": "https://the url of sd2jknr.jpg" }
        ]
        

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
        { 
            "id": "f1disy1", 
            "url": "https://the url of f1disy1.jpg",
            "likes_count": 241           
        }
        
### Comment on a Photo

-   Endpoint: `POST /api/photos/{photoId}/comments`
-   Description: Add a comment to a photo.
-   Path Parameter:
    -   `photoId` - The ID of the photo to comment on.
-   Request Body: JSON object
    -   Example: `[
                {"id": "fs24nj", "content": "this is a commento to your foto", "userId": "df234n", "userName": "John" },
                {"id": "wsdrvv", "content": "another cool comment", "userId": "u734bn", "userName": "Ringo" },
                {"id": "42vgwa", "content": "another cool comment", "userId": "dasdd", "userName": "Paul" },
                {"id": "324fhi", "content": "another cool comment", "userId": "uasdn", "userName": "George" }
            ]`
-   Response:
    -   HTTP 200 OK if the comment is successfully added.
    -   Response Body: JSON object containing the updated photo details.

### Like a Photo

-   Endpoint: `POST /api/photos/{photoId}/like`
-   Description: Like a photo.
-   Path Parameter:
    -   `photoId` - The ID of the photo to like.
-   Response:
    -   HTTP 200 OK if the like is successfully added.
    -   Response Body: JSON object containing the updated photo details.

### Mark a Photo as Private

-   Endpoint: `PATCH /api/photos/{photoId}`
-   Description: Mark a photo as private.
-   Path Parameter:
    -   `photoId` - The ID of the photo to update.
-   Request Body: JSON object
    -   Example: `{ "isPrivate": true }`
-   Response:
    -   HTTP 200 OK if the photo is successfully updated.
    -   Response Body: JSON object containing the updated photo details.

### Follow/Unfollow an User

-   Endpoint: `POST /api/users/{userId}/follow`
    -   To follow a user.
-   Endpoint: `POST /api/users/{userId}/unfollow`
    -   To unfollow a user.
-   Path Parameter:
    -   `userId` - The ID of the user to follow/unfollow.
-   Response:
    -   HTTP 200 OK if the operation is successful.
    -   Response Body: JSON object confirming the follow/unfollow action.

### Delete a Photo

-   Endpoint: `DELETE /api/photos/{photoId}`
-   Description: Delete a photo from the Photo Social Network.
-   Path Parameter:
    -   `photoId` - The ID of the photo to delete.
