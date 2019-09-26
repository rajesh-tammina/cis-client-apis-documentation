# Render Filtered Aid Index

Description: The client needs to display a filtered index of aid items.

- [] Request the filtered Aid Index. [Filtered Index Endpoint Readme](/aid_api/aid_index_aid_get.md).
    - [] Use the base POST /aid with filter options provided to retrieve page 1 of filtered aid items index.
- [] If there are more aid items past page 1 and the client needs to access more filtered aid items use the POST /aid with the same filter options except page which should be itterated by 1.

![Alt text](/aid-api/assets/user-story-index-2.png?raw=true)

````
sequenceDiagram
    participant Client
    participant POST /aid
    participant DONE
    Client->>POST /aid: POST for First Page Of Filtered Aid Index
    Note right of POST /aid: See  <br/>aid_index_aid_post.md
    Client->> POST /aid: [ NEXT PAGE? ] Need To Display More Filtered Aid Items?
    loop NEXT PAGE Yes
         POST /aid->> POST /aid: Get next page of filtered aid index
    end
     POST /aid-->>DONE: [ NEXT PAGE No ]
````