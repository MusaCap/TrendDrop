# 🗃️ TrendDrop Data Model

A hybrid data architecture using MongoDB (for flexible content/trend storage) and PostgreSQL (for user management and relationships).

---

## 1. User

Stores user info and connected social media accounts.

```json
{
  "_id": "uuid",
  "name": "string",
  "email": "string",
  "role": "creator | admin",
  "connected_platforms": [
    {
      "platform": "tiktok | youtube | instagram",
      "oauth_token": "string",
      "account_id": "string",
      "username": "string"
    }
  ],
  "created_at": "datetime",
  "last_login": "datetime"
}
```

---

## 2. VideoUpload

Represents a short-form video uploaded by a user.

```json
{
  "_id": "uuid",
  "user_id": "uuid",
  "file_url": "string",
  "duration_seconds": "int",
  "transcript": "string",
  "summary": "string",
  "thumbnail_url": "string",
  "language": "string",
  "created_at": "datetime",
  "status": "uploaded | processing | ready | published"
}
```

---

## 3. TrendTopic

Represents a trending keyword, hashtag, or news headline.

```json
{
  "_id": "uuid",
  "source": "tiktok | twitter | youtube | google_news",
  "platform": "tiktok | youtube | instagram | general",
  "trend_type": "hashtag | keyword | headline",
  "title": "string",
  "tags": ["string"],
  "matched_keywords": ["string"],
  "score": "float",
  "fetched_at": "datetime"
}
```

---

## 4. PlatformMetadata

Stores generated titles, descriptions, and hashtags per platform.

```json
{
  "_id": "uuid",
  "video_id": "uuid",
  "platform": "tiktok | youtube | instagram",
  "title": "string",
  "description": "string",
  "hashtags": ["string"],
  "cta": "string",
  "thumbnail_url": "string",
  "trend_matches": ["trend_id"],
  "generated_at": "datetime",
  "is_edited_by_user": "boolean"
}
```

---

## 5. PostSchedule

Tracks when and where a video is or will be published.

```json
{
  "_id": "uuid",
  "video_id": "uuid",
  "platform": "tiktok | youtube | instagram",
  "scheduled_at": "datetime",
  "status": "scheduled | published | failed",
  "post_id": "string",
  "performance_metrics": {
    "views": "int",
    "likes": "int",
    "shares": "int",
    "comments": "int",
    "engagement_rate": "float"
  }
}
```

---

## 6. FeedbackSignal (Optional - Learning Loop)

Captures metadata performance for improving AI recommendations.

```json
{
  "_id": "uuid",
  "platform_metadata_id": "uuid",
  "engagement_score": "float",
  "positive_feedback": ["string"],
  "negative_feedback": ["string"],
  "timestamp": "datetime"
}
```

---

## 🔄 Relationships

- `User` → uploads → `VideoUpload`
- `VideoUpload` → has many → `PlatformMetadata`
- `PlatformMetadata` → generated from → `TrendTopic`
- `PlatformMetadata` → scheduled via → `PostSchedule`
- `PostSchedule` → returns → `performance_metrics`
- `FeedbackSignal` → refines → `PlatformMetadata` (learning loop)

---

## 🧠 Implementation Notes

- Use **MongoDB** for `VideoUpload`, `TrendTopic`, `PlatformMetadata` (flexible, nested AI content)
- Use **PostgreSQL** or **Firebase Auth** for `User` and access control
- Use **Redis** for caching trends and managing job queues
- Use **Pinecone/Weaviate** (optional) for semantic video-to-trend vector search
