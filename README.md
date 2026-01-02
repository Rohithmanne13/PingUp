# PingUp

> A full-stack real-time social networking platform built with React, Express, and MongoDB. Features include instant messaging using Server-Sent Events, user connections and follow system, posts and stories with image uploads, automated background job processing for scheduled tasks, and cloud-based media storage with automatic image optimization.

## ✨ Key Features

- 🔐 **Secure Authentication** - Clerk-based user authentication
- 👥 **Social Connections** - Send/accept connection requests with email notifications
- 📝 **Posts & Feed** - Create posts with images, personalized feed from your network
- 📖 **Stories** - Share temporary stories (auto-delete after 24 hours)
- 💬 **Real-Time Messaging** - Instant messaging using Server-Sent Events (SSE)
- 🖼️ **Image Optimization** - Automatic WebP conversion with quality and size optimization
- 📧 **Email Notifications** - Automated reminders and daily message digests
- 📱 **Responsive Design** - Modern UI with TailwindCSS

## 🛠 Tech Stack

**Frontend:** React 19 • Vite • Redux Toolkit • TailwindCSS • Clerk Auth • Axios

**Backend:** Node.js • Express 5 • MongoDB • Mongoose • Clerk • Multer

**Services:** ImageKit (storage) • Inngest (background jobs) • Nodemailer (emails)

## 📁 Project Structure

```
 client/                          # React Frontend
   ├── src/
   │   ├── api/                     # Axios configuration
   │   ├── app/                     # Redux store
   │   ├── components/              # Reusable components
   │   │   ├── Loading.jsx
   │   │   ├── Notification.jsx
   │   │   ├── PostCard.jsx
   │   │   ├── ProfileModal.jsx
   │   │   ├── Sidebar.jsx
   │   │   ├── StoriesBar.jsx
   │   │   └── UserCard.jsx
   │   ├── features/                # Redux slices
   │   │   ├── connections/
   │   │   ├── messages/
   │   │   └── user/
   │   ├── pages/                   # Route pages
   │   │   ├── Feed.jsx
   │   │   ├── Messages.jsx
   │   │   ├── Connections.jsx
   │   │   ├── Discover.jsx
   │   │   └── Profile.jsx
   │   └── App.jsx
   └── package.json
 server/                          # Express Backend
    ├── configs/                     # DB, ImageKit, Email configs
    ├── controllers/                 # Business logic
    │   ├── userController.js
    │   ├── postController.js
    │   ├── storyController.js
    │   └── messageController.js
    ├── models/                      # MongoDB schemas
    │   ├── User.js
    │   ├── Post.js
    │   ├── Story.js
    │   ├── Message.js
    │   └── Connection.js
    ├── routes/                      # API endpoints
    ├── inngest/                     # Background jobs
    └── server.js
```

## 🚀 Quick Start

### Prerequisites
- Node.js v16+
- MongoDB (Atlas or local)
- Clerk, ImageKit, and Inngest accounts

### Installation

```bash
# Clone repository
git clone <repository-url>
cd pingup-full-stack
    
# Install dependencies
cd client && npm install
cd server && npm install

# Run development servers
cd server && npm run server    # Backend on port 4000
cd client && npm run dev       # Frontend on port 5173
```

### Environment Variables

**Client (.env)**
```env
VITE_CLERK_PUBLISHABLE_KEY=your_clerk_key
VITE_BASEURL=your_backend_url
```

**Server (.env)**
```env
MONGODB_URI=your_mongodb_uri
CLERK_PUBLISHABLE_KEY=your_clerk_key
CLERK_SECRET_KEY=your_clerk_secret
IMAGEKIT_PUBLIC_KEY=your_imagekit_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
IMAGEKIT_URL_ENDPOINT=your_imagekit_endpoint
EMAIL_USER=your_email
EMAIL_PASS=your_email_password
INNGEST_EVENT_KEY=your_inngest_key
FRONTEND_URL=your_frontend_url
```

## 📡 API Endpoints

| Route | Method | Description |
|-------|--------|-------------|
| `/api/user/data/:userId` | GET | Get user profile |
| `/api/user/update` | PUT | Update profile |
| `/api/user/discover` | GET | Search users |
| `/api/user/follow` | POST | Follow user |
| `/api/user/connection/send` | POST | Send connection request |
| `/api/user/connections` | GET | Get connections |
| `/api/post/add` | POST | Create post |
| `/api/post/feed` | GET | Get feed posts |
| `/api/post/like` | POST | Like/unlike post |
| `/api/story/add` | POST | Create story |
| `/api/story/get` | GET | Get stories |
| `/api/message/send` | POST | Send message |
| `/api/message/:userId` | GET | SSE endpoint |

## 🎯 Core Functionality

### Real-Time Messaging
- Uses **Server-Sent Events (SSE)** for instant message delivery
- In-app toast notifications for new messages
- Message read/unread status tracking

### Background Jobs (Inngest)
- **User Sync**: Auto-sync user data from Clerk webhooks
- **Story Deletion**: Auto-delete stories after 24 hours
- **Email Reminders**: Send connection request reminders after 24 hours
- **Notifications**: Unseen message notifications are shown in real-time during app usage

### Image Processing
- Automatic upload to ImageKit
- WebP conversion for optimal performance
- Quality and size optimization (max 1280px width)

## 📝 Database Models

- **User**: Profile, followers, following, connections
- **Post**: Content, images, likes, post type
- **Story**: Media, views, auto-delete timestamp
- **Message**: Text/image, sender/receiver, seen status
- **Connection**: Request status (pending/accepted)



