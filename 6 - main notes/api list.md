## Index: [[Reel app]]

Here’s a comprehensive set of RESTful API routes you’ll likely need for your social‑video app. Feel free to adapt paths or HTTP methods to fit your conventions or switch to GraphQL if you prefer.

---

## 1. **Authentication & Users**

| Method   | Path                 | Description                                | check   |
| -------- | -------------------- | ------------------------------------------ | ------- |
| `POST`   | `/api/auth/signup`   | Create a new user account                  | done    |
| `POST`   | `/api/auth/login`    | Authenticate user, return JWT/session      | no need |
| `GET`    | `/api/users`         | List all users                             | no need |
| `GET`    | `/api/users/:userid` | Get profile (incl. creator/viewer data)    | done    |
| `PUT`    | `/api/users/:userid` | Update user profile                        | done    |
| `DELETE` | `/api/users/:userid` | Delete user (cascade interactions, videos) | done    |

---

## 2. **Videos**

| Method   | Path                   | Description                              | Check     |
| -------- | ---------------------- | ---------------------------------------- | --------- |
| `GET`    | `/api/videos`          | List all videos (with uploader info)     | done      |
| `GET`    | `/api/videos/:videoid` | Get video details + interactions counts  | done      |
| `POST`   | `/api/videos`          | Upload new video                         | done      |
| `PUT`    | `/api/videos/:videoid` | Update video metadata (e.g. description) | no needed |
| `DELETE` | `/api/videos/:videoid` | Delete video (cascade interactions)      | done      |

---

## 3. **Interactions (Generalized)**

| Method   | Path                                | Description                                  |
| -------- | ----------------------------------- | -------------------------------------------- |
| `GET`    | `/api/interactions`                 | List all interactions (filterable via query) |
| `GET`    | `/api/interactions/:interaction_id` | Get a single interaction record              |
| `POST`   | `/api/interactions`                 | Create an interaction (body includes `type`) |
| `DELETE` | `/api/interactions/:interaction_id` | Remove an interaction (uncomment/unlike)     |

---

### 3a. **Comments**

| Method   | Path                            | Description                                        |
| -------- | ------------------------------- | -------------------------------------------------- |
| `GET`    | `/api/videos/:videoid/comments` | List comments on a video (includes commenter info) |
| `POST`   | `/api/videos/:videoid/comments` | Add a comment (body: `{ user_id, comment_text }`)  |
| `PUT`    | `/api/comments/:interaction_id` | Edit a comment                                     |
| `DELETE` | `/api/comments/:interaction_id` | Delete a comment                                   |

---

### 3b. **Likes**

| Method   | Path                                  | Description                        |
| -------- | ------------------------------------- | ---------------------------------- |
| `GET`    | `/api/videos/:videoid/likes/count`    | Get like count for a video         |
| `POST`   | `/api/videos/:videoid/likes`          | Like a video (body: `{ user_id }`) |
| `DELETE` | `/api/videos/:videoid/likes/:user_id` | Unlike a video                     |

---

## 4. **Profiles & Dashboards** (not now)

|Method|Path|Description|
|---|---|---|
|`GET`|`/api/users/:userid/dashboard`|Get combined stats (videos, interactions, etc.)|
|`GET`|`/api/users/:userid/creator-stats`|Get creator-specific stats (uploads, views)|
|`GET`|`/api/users/:userid/viewer-stats`|Get viewer-specific stats (interactions)|

---

## 5. **Leaderboards & Analytics** (not now)

| Method | Path                               | Description                             |
| ------ | ---------------------------------- | --------------------------------------- |
| `GET`  | `/api/leaderboard/most-active`     | Top N users by total_interactions       |
| `GET`  | `/api/leaderboard/top-creators`    | Top N users by total_videos_uploaded    |
| `GET`  | `/api/analytics/video-performance` | Aggregate for all videos (views, likes) |

---

## 6. **Administration & Utilities** (not now)

| Method   | Path                         | Description                               |
| -------- | ---------------------------- | ----------------------------------------- |
| `GET`    | `/api/health`                | Health check                              |
| `POST`   | `/api/seed`                  | Seed database with sample data (dev only) |
| `DELETE` | `/api/interactions/truncate` | Wipe interactions (admin)                 |

---

### 🔄 Notes & Conventions

- **Authentication**: Protect write routes (POST/PUT/DELETE) behind JWT/session middleware.
    
- **Pagination**: Use query parameters `?page=&limit=` on list endpoints.
    
- **Filtering/Sorting**: e.g. `/api/videos?uploader_id=<>&sort=views_desc`.
    
- **Error Handling**: Standardize error codes (e.g. 400 for validation, 404 for not found).
    

Feel free to adjust naming (e.g. `/comments` vs. nested under `/videos`) or add GraphQL equivalents. Let me know if you want sample controller/handler stubs in your framework of choice!


### 🚀 2. **Sign In & Get JWT Token**
Create a `POST` request in Postman:
	
- **URL**: `http://localhost:3000/api/auth/callback/credentials`

- **Body** → `x-www-form-urlencoded`:

    - `csrfToken`: `GET` it from `/api/auth/csrf`
    
    - `email`: `your email`
    
    - `password`: `your password`