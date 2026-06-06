# 🏠 HomeNest - Backend Server

Backend API server for HomeNest, a real estate listing platform where property owners can post rentals/sale listings and users can browse, search, and filter properties.

## ✨ Features

- **Full CRUD Operations**: Create, Read, Update, and Delete property listings with complete data validation
- **Authentication & Authorization**: Firebase Admin SDK token verification with JWT cookie-based sessions; ownership verification ensures users can only modify their own properties
- **Advanced Search & Sort**: Backend-powered search by property name (case-insensitive regex), sort by price or date (ascending/descending), and filter by category — all processed server-side via MongoDB queries
- **Ratings & Reviews System**: Users can rate properties (1–5 stars) with written reviews; average ratings are calculated per property; self-review prevention is enforced
- **Production-Ready Security**: Helmet security headers, HTTP-only secure cookies with SameSite policy, CORS whitelisting, input validation, and graceful error handling
- **Optimized MongoDB**: Pre-built indexes on frequently queried fields (email, category, price, date) for fast performance; pagination support with total count metadata
- **Vercel Deployment Ready**: Pre-configured `vercel.json` for seamless serverless deployment

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Node.js | Runtime |
| Express.js | Web framework |
| MongoDB | Database (via native driver) |
| Firebase Admin SDK | Token verification |
| JSON Web Tokens | Session management |
| Helmet | Security headers |
| CORS | Cross-origin configuration |

---


### Properties
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| GET | `/api/properties` | ❌ | All properties (search, sort, filter, paginate) |
| GET | `/api/properties/featured` | ❌ | 6 newest properties |
| GET | `/api/properties/user/:email` | ✅ | User's properties |
| GET | `/api/properties/:id` | ✅ | Property details |
| POST | `/api/properties` | ✅ | Add property |
| PUT | `/api/properties/:id` | ✅ | Update property (owner only) |
| DELETE | `/api/properties/:id` | ✅ | Delete property (owner only) |

### Reviews
| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| POST | `/api/reviews` | ✅ | Add review/rating |
| GET | `/api/reviews/property/:id` | ❌ | Reviews for a property |
| GET | `/api/reviews/user/:email` | ✅ | User's reviews |
| DELETE | `/api/reviews/:id` | ✅ | Delete review (author only) |

---

## 🚀 Getting Started

### Prerequisites
- Node.js v18+
- MongoDB Atlas account
- Firebase project (optional, for Admin SDK)

### Installation

```bash
git clone <your-repo-url>
cd server
npm install
```

## 📁 Project Structure

```
server/
├── index.js                # Express app entry point
├── package.json
├── vercel.json             # Vercel deployment config
├── .env                    # Environment variables
├── .gitignore
├── README.md
├── config/
│   └── firebase.js         # Firebase Admin SDK setup
├── middleware/
│   └── verifyToken.js      # JWT/Firebase auth middleware
└── routes/
    ├── auth.js             # Auth token routes
    ├── users.js            # User profile routes
    ├── properties.js       # Property CRUD routes
    └── reviews.js          # Review/rating routes
```
