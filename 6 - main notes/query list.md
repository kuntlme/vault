## Index: [[Reel app]]

Below is a comprehensive list of the Prisma Client queries you’ll likely need in your video-social app. You can copy these directly into your project’s service layer (e.g. under `/lib/prisma.ts` or similar) and adjust as needed.

---

## 1. User CRUD

```ts
// Create a new user
const createUser = (data: {
  profilename: string;
  username: string;
  joining_date: Date;
  location: string;
}) =>
  prisma.user.create({ data });

// Read user by ID (with profile, creator & viewer info)
const getUserById = (userid: string) =>
  prisma.user.findUnique({
    where: { userid },
    include: { creator: true, viewer: true },
  });

// Read user by username
const getUserByUsername = (username: string) =>
  prisma.user.findUnique({ where: { username } });

// Update user
const updateUser = (userid: string, data: Partial<{
  profilename: string;
  username: string;
  joining_date: Date;
  location: string;
}>) =>
  prisma.user.update({ where: { userid }, data });

// Delete user
const deleteUser = (userid: string) =>
  prisma.user.delete({ where: { userid } });
```

---

## 2. Video CRUD

```ts
// Create a new video
const createVideo = (data: {
  uploader_id: string;
  description: string;
  sharelink: string;
  viewcount?: number;      // defaults to 0 if you like
  uploaded_at?: Date;      // defaults to now()
}) =>
  prisma.video.create({ data });

// Get a video (with uploader & interactions)
const getVideo = (videoid: string) =>
  prisma.video.findUnique({
    where: { videoid },
    include: {
      uploader: true,
      interactions: {
        include: { comment: true, like: true },
      },
    },
  });

// List videos by user (most-recent first)
const listVideosByUser = (uploader_id: string) =>
  prisma.video.findMany({
    where: { uploader_id },
    orderBy: { uploaded_at: 'desc' },
  });

// Update video (e.g. increment viewcount)
const incrementVideoViews = (videoid: string) =>
  prisma.video.update({
    where: { videoid },
    data: { viewcount: { increment: 1 } },
  });

// Delete video
const deleteVideo = (videoid: string) =>
  prisma.video.delete({ where: { videoid } });
```

---

## 3. Interaction / Comment / Like

### a) Create an Interaction (Comment or Like)

```ts
// Common helper
async function createInteraction(data: {
  user_id: string;
  video_id: string;
  type: 'comment' | 'like';
  comment_text?: string;
}) {
  // 1) Create Interaction row
  const interaction = await prisma.interaction.create({
    data: {
      user_id: data.user_id,
      video_id: data.video_id,
      interaction_at: new Date(),
      type: data.type,
      comment: data.type === 'comment'
        ? { create: { comment_text: data.comment_text! } }
        : undefined,
      like: data.type === 'like' ? { create: {} } : undefined,
    },
  });

  // 2) Upsert Viewer.total_interactions
  await prisma.viewer.upsert({
    where: { userid: data.user_id },
    update: { total_interactions: { increment: 1 } },
    create: { userid: data.user_id, total_interactions: 1 },
  });

  return interaction;
}
```

### b) Read comments / likes for a video

```ts
// All comments on a video (with user info)
const listCommentsForVideo = (video_id: string) =>
  prisma.comment.findMany({
    where: { interaction: { video_id, type: 'comment' } },
    include: { interaction: { include: { user: true } } },
  });

// Count likes on a video
const countLikesForVideo = (video_id: string) =>
  prisma.like.count({
    where: { interaction: { video_id, type: 'like' } },
  });

// Check if given user liked a video
const hasUserLikedVideo = (user_id: string, video_id: string) =>
  prisma.like.findUnique({
    where: {
      interaction_id: `${user_id}_${video_id}`, // if you override composite PK
    },
  });
```

---

## 4. Creator / Viewer Metrics

```ts
// Increment creator’s total_videos_uploaded when uploading a video
const bumpCreatorCount = async (uploader_id: string) => {
  await prisma.creator.upsert({
    where: { userid: uploader_id },
    update: { total_videos_uploaded: { increment: 1 } },
    create: { userid: uploader_id, total_videos_uploaded: 1 },
  });
};

// Fetch Creator stats for a user
const getCreatorStats = (userid: string) =>
  prisma.creator.findUnique({ where: { userid } });

// Fetch Viewer stats for a user
const getViewerStats = (userid: string) =>
  prisma.viewer.findUnique({ where: { userid } });
```

---

## 5. Analytics & Leaderboards

```ts
// Top 5 active viewers
const getTopActiveViewers = () =>
  prisma.viewer.findMany({
    orderBy: { total_interactions: 'desc' },
    take: 5,
    include: { user: true },
  });

// Top 5 creators
const getTopCreators = () =>
  prisma.creator.findMany({
    orderBy: { total_videos_uploaded: 'desc' },
    take: 5,
    include: { user: true },
  });
```

---

## 6. Putting It All Together

You’ll call these in your service/controller layers:

1. **User signup** → `createUser`
    
2. **Video upload** → `createVideo` + `bumpCreatorCount`
    
3. **View video** → `getVideo` + `incrementVideoViews`
    
4. **Comment/Like** → `createInteraction(...)`
    
5. **Profile** → `getUserById` (with creator/viewer)
    
6. **Leaderboards** → `getTopActiveViewers`, `getTopCreators`
    

---

Feel free to adapt naming or composite-key logic (e.g. how you derive the `interaction_id` in `Like.findUnique`) to your conventions. Let me know if you need implementation details (e.g. controllers, routes, or Nexus/GraphQL bindings)!