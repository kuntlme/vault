Here’s a **clear mapping of your API routes to their corresponding Prisma query functions** based on your social video app structure.

---

## ✅ API Routes and Their Query Functions

|HTTP Method|API Route|Function / Prisma Query Used|
|---|---|---|
|`POST`|`/api/auth/signup`|`prisma.user.create()`|
|`POST`|`/api/auth/login`|`prisma.user.findUnique()` (to verify credentials)|
|`GET`|`/api/users`|`prisma.user.findMany()`|
|`GET`|`/api/users/:userid`|`prisma.user.findUnique({ include: { creator, viewer } })`|
|`PUT`|`/api/users/:userid`|`prisma.user.update()`|
|`DELETE`|`/api/users/:userid`|`prisma.user.delete()`|

---

### 🎥 Video Routes

| HTTP Method | API Route              | Function / Prisma Query Used                             |
| ----------- | ---------------------- | -------------------------------------------------------- |
| `GET`       | `/api/videos`          | `prisma.video.findMany({ include: { uploader: true } })` |
| `GET`       | `/api/videos/:videoid` | `prisma.video.findUnique({ where: { videoid } })`        |
| `POST`      | `/api/videos`          | `prisma.video.create()`+ `prisma.creator.upsert()`       |
| `PUT`       | `/api/videos/:videoid` | `prisma.video.update()`                                  |
| `DELETE`    | `/api/videos/:videoid` | `prisma.video.delete()`                                  |

---

### 💬 Comment Routes

| HTTP Method | API Route                       | Function / Prisma Query Used                                                                                     |
| ----------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `GET`       | `/api/videos/:videoid/comments` | `prisma.comment.findMany()` via `interaction.video_id`                                                           |
| `POST`      | `/api/videos/:videoid/comments` | `prisma.interaction.create({ data: { type: 'comment' } })` + `prisma.comment.create()`+ `prisma.viewer.upsert()` |
| `PUT`       | `/api/comments/:interaction_id` | `prisma.comment.update()`                                                                                        |
| `DELETE`    | `/api/comments/:interaction_id` | `prisma.comment.delete()` + `prisma.interaction.delete()`                                                        |

---

### ❤️ Like Routes

|HTTP Method|API Route|Function / Prisma Query Used|
|---|---|---|
|`GET`|`/api/videos/:videoid/likes/count`|`prisma.interaction.count({ where: { type: 'like' } })`|
|`POST`|`/api/videos/:videoid/likes`|`prisma.interaction.create({ type: 'like' })` + `prisma.like.create()` + `prisma.viewer.upsert()`|
|`DELETE`|`/api/videos/:videoid/likes/:user_id`|`prisma.like.delete()` + `prisma.interaction.delete()`|

---

### 📊 Analytics / Leaderboards

|HTTP Method|API Route|Function / Prisma Query Used|
|---|---|---|
|`GET`|`/api/leaderboard/most-active`|`prisma.viewer.findMany({ orderBy: { total_interactions: 'desc' } })`|
|`GET`|`/api/leaderboard/top-creators`|`prisma.creator.findMany({ orderBy: { total_videos_uploaded: 'desc' } })`|
|`GET`|`/api/analytics/video-performance`|Aggregated `findMany()` or raw query if needed|

---

### 🧑 Profile / Dashboard

| HTTP Method | API Route                          | Function / Prisma Query Used                                       |
| ----------- | ---------------------------------- | ------------------------------------------------------------------ |
| `GET`       | `/api/users/:userid/dashboard`     | `prisma.user.findUnique({ include: { videos, viewer, creator } })` |
| `GET`       | `/api/users/:userid/creator-stats` | `prisma.creator.findUnique()`                                      |
| `GET`       | `/api/users/:userid/viewer-stats`  | `prisma.viewer.findUnique()`                                       |

---

### 🛠 Dev/Utility

|Method|API Route|Function / Prisma Query Used|
|---|---|---|
|`POST`|`/api/seed`|`prisma.*.createMany()` or scripted seeds|
|`GET`|`/api/health`|return `{ status: "ok" }`|
|`DELETE`|`/api/interactions/truncate`|`prisma.interaction.deleteMany()`|

---

Would you like me to generate actual controller function stubs (e.g. `POST /api/videos` handler) in TypeScript/Next.js style for any of these?