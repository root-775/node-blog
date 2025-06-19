# Blog App 📝

A modern full-stack blog application built with Next.js and Express.js, featuring user authentication, post management, and a responsive design.

## 🌟 Features

### Frontend (Next.js 15)
- **Responsive Design**: Built with Tailwind CSS for mobile-first responsive layouts
- **User Authentication**: Secure login/register system with JWT tokens
- **Protected Routes**: Route protection for authenticated users
- **Post Management**: Create, read, update, delete (CRUD) operations for blog posts
- **Dashboard**: Personal dashboard for managing user's posts
- **Real-time UI Updates**: Instant feedback on user actions
- **TypeScript Support**: Full TypeScript integration for type safety

### Backend (Express.js)
- **RESTful API**: Well-structured API endpoints for all operations
- **MongoDB Integration**: Database operations using Mongoose ODM
- **JWT Authentication**: Secure token-based authentication system
- **Password Hashing**: Secure password storage using bcryptjs
- **CORS Support**: Cross-Origin Resource Sharing enabled
- **Input Validation**: Server-side validation for all inputs
- **Error Handling**: Comprehensive error handling and logging

### Core Functionality
- **User Registration vent & Login**: Secure user account creation and authentication
- **Post Creation**: Rich text post creation with title and content
- **Post Publishing**: Draft/publish system for posts
- **Post Management**: Edit, delete, and toggle publish status
- **Public Blog**: View published posts without authentication
- **User Dashboard**: Manage personal posts with status indicators
- **Post Viewing**: Individual post pages with author information

## Tech Stack

### Frontend (Next.js)
- Next.js 15 with App Router
- TypeScript
- Tailwind CSS
- Axios for API calls
- React Context for state management

### Backend (Node.js API)
- Express.js
- MongoDB with Mongoose
- JWT Authentication
- bcryptjs for password hashing
- CORS enabled

## Project Structure

```
blog-app/
├── src/                          # Next.js frontend
│   ├── app/                      # App Router pages
│   │   ├── dashboard/            # Protected dashboard
│   │   ├── login/                # Login page
│   │   ├── register/             # Registration page
│   │   └── posts/                # Post-related pages
│   │       ├── create/           # Create post
│   │       ├── edit/[id]/        # Edit post
│   │       └── [id]/             # View post
│   ├── components/               # Reusable components
│   └── contexts/                 # React contexts
└── api/                          # Node.js backend
    ├── models/                   # MongoDB models
    ├── routes/                   # API routes
    ├── middleware/               # Custom middleware
    └── server.js                 # Main server file
```

## Setup Instructions

### Prerequisites
- Node.js (v18+)
- MongoDB (local or MongoDB Atlas)
- npm or yarn

### 1. Install Dependencies

#### Frontend (Next.js)
```bash
cd blog-app
npm install
```

#### Backend (API)
```bash
cd blog-app/api
npm install
```

### 2. Environment Variables

#### Frontend (.env.local)
```
NEXT_PUBLIC_API_URL=http://localhost:5000/api
```

#### Backend (api/.env)
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/blog-app
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
NODE_ENV=development
```

### 3. Start MongoDB
Make sure MongoDB is running on your system:
```bash
# If using local MongoDB
mongod

# Or use MongoDB Atlas cloud database
# Update MONGODB_URI in api/.env with your Atlas connection string
```

### 4. Run the Application

#### Start Backend API (Terminal 1)
```bash
cd blog-app/api
npm run dev
```
API will run on http://localhost:5000

#### Start Frontend (Terminal 2)
```bash
cd blog-app
npm run dev
```
Frontend will run on http://localhost:3000

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user (protected)

### Posts
- `GET /api/posts` - Get all published posts (public)
- `GET /api/posts/:id` - Get single post (public)
- `GET /api/posts/user/my-posts` - Get user's posts (protected)
- `POST /api/posts` - Create new post (protected)
- `PUT /api/posts/:id` - Update post (protected, author only)
- `DELETE /api/posts/:id` - Delete post (protected, author only)

## Usage

1. **Register/Login**: Create an account or login with existing credentials
2. **Dashboard**: View and manage your posts after logging in
3. **Create Posts**: Write new blog posts with draft/publish options
4. **Edit Posts**: Modify your existing posts
5. **Public View**: All published posts are visible on the home page

## Key Features Explained

### Authentication Flow
- Users register/login through forms
- JWT tokens are stored in localStorage
- Axios interceptors handle authentication headers
- Protected routes redirect unauthenticated users

### Post Management
- Authors can create, edit, and delete their own posts
- Posts can be saved as drafts or published immediately
- Published posts appear on the public home page
- Only authors can modify their own posts

### Security
- Passwords are hashed with bcryptjs
- JWT tokens for stateless authentication
- Protected routes on both frontend and backend
- Input validation and error handling

## Customization

- Modify the UI by editing Tailwind classes
- Add new features by creating additional API routes
- Extend the Post model for additional fields (tags, categories, etc.)
- Implement email verification, password reset, etc.

## Troubleshooting

- Ensure MongoDB is running and accessible
- Check that environment variables are set correctly
- Verify API and frontend are running on different ports
- Check browser console for any JavaScript errors
- Ensure CORS is properly configured for your domain

## 🛠️ Technology Stack

### Frontend
- **Framework**: Next.js 15 with App Router
- **Language**: TypeScript
- **Styling**: Tailwind CSS 4
- **HTTP Client**: Axios
- **Form Handling**: React Hook Form
- **State Management**: React Context API
- **UI Components**: Custom React components

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js 5
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JSON Web Tokens (JWT)
- **Password Hashing**: bcryptjs
- **Environment Variables**: dotenv
- **Development**: nodemon for hot reloading
- **Security**: CORS middleware

## 📁 Detailed Project Structure

```
blog-app/
├── api/                          # Backend Express.js server
│   ├── middleware/
│   │   └── auth.js              # JWT authentication middleware
│   ├── models/
│   │   ├── User.js              # User database model
│   │   └── Post.js              # Post database model
│   ├── routes/
│   │   ├── auth.js              # Authentication routes
│   │   └── posts.js             # Post management routes
│   ├── node_modules/            # Backend dependencies
│   ├── package.json             # Backend dependencies and scripts
│   └── server.js                # Express server entry point
├── src/                         # Frontend Next.js application
│   ├── app/                     # Next.js App Router
│   │   ├── dashboard/
│   │   │   └── page.tsx         # User dashboard page
│   │   ├── login/
│   │   │   └── page.tsx         # Login page
│   │   ├── posts/
│   │   │   ├── [id]/
│   │   │   │   └── page.tsx     # Individual post view
│   │   │   ├── create/
│   │   │   │   └── page.tsx     # Create new post
│   │   │   └── edit/[id]/
│   │   │       └── page.tsx     # Edit existing post
│   │   ├── register/
│   │   │   └── page.tsx         # Registration page
│   │   ├── favicon.ico
│   │   ├── globals.css          # Global styles
│   │   ├── layout.tsx           # Root layout component
│   │   └── page.tsx             # Home page
│   ├── components/
│   │   ├── Navigation.tsx       # Navigation bar component
│   │   └── ProtectedRoute.tsx   # Route protection wrapper
│   └── contexts/
│       └── AuthContext.tsx      # Authentication context
├── public/                      # Static assets
├── node_modules/                # Frontend dependencies
├── .gitignore                   # Git ignore rules
├── eslint.config.mjs           # ESLint configuration
├── next.config.ts              # Next.js configuration
├── package.json                # Frontend dependencies and scripts
├── postcss.config.mjs          # PostCSS configuration
├── tsconfig.json               # TypeScript configuration
└── README.md                   # Project documentation
```

## 📚 API Documentation

### Authentication Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |
| GET | `/api/auth/me` | Get current user | Yes |

### Post Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/posts` | Get all published posts | No |
| GET | `/api/posts/:id` | Get single post | No |
| GET | `/api/posts/user/my-posts` | Get user's posts | Yes |
| POST | `/api/posts` | Create new post | Yes |
| PUT | `/api/posts/:id` | Update post | Yes (Author only) |
| DELETE | `/api/posts/:id` | Delete post | Yes (Author only) |

### Request/Response Examples

**User Registration**
```json
POST /api/auth/register
{
  "username": "johndoe",
  "email": "john@example.com",
  "password": "securepassword"
}

Response:
{
  "message": "User created successfully",
  "token": "jwt-token-here",
  "user": {
    "id": "user-id",
    "username": "johndoe",
    "email": "john@example.com"
  }
}
```

**Create Post**
```json
POST /api/posts
Authorization: Bearer jwt-token-here
{
  "title": "My First Blog Post",
  "content": "This is the content of my blog post...",
  "published": true
}

Response:
{
  "message": "Post created successfully",
  "post": {
    "_id": "post-id",
    "title": "My First Blog Post",
    "content": "This is the content...",
    "author": {
      "username": "johndoe"
    },
    "published": true,
    "createdAt": "2024-01-01T00:00:00.000Z"
  }
}
```

## 🎨 User Interface

### Pages Overview

1. **Home Page (`/`)**: Displays all published blog posts in a card layout
2. **Login Page (`/login`)**: User authentication form
3. **Register Page (`/register`)**: User registration form
4. **Dashboard (`/dashboard`)**: User's personal post management area
5. **Create Post (`/posts/create`)**: Form to create new blog posts
6. **Edit Post (`/posts/edit/[id]`)**: Form to edit existing posts
7. **View Post (`/posts/[id]`)**: Individual post display page

### Key Components

- **Navigation**: Responsive navigation bar with authentication state
- **AuthContext**: Global authentication state management
- **ProtectedRoute**: Higher-order component for route protection

## 🔒 Security Features

- **Password Hashing**: All passwords are hashed using bcryptjs with salt rounds
- **JWT Tokens**: Secure token-based authentication with 7-day expiration
- **Protected Routes**: Frontend and backend route protection
- **Input Validation**: Server-side validation for all user inputs
- **CORS Configuration**: Proper cross-origin resource sharing setup
- **Authorization Checks**: Users can only modify their own posts

## 🧪 Development Guidelines

### Code Style
- TypeScript for type safety
- ESLint for code linting
- Consistent naming conventions
- Component-based architecture

### Best Practices
- Separation of concerns (frontend/backend)
- RESTful API design
- Error handling and user feedback
- Responsive design principles
- Secure authentication practices

## 📎 Production Deployment

### Frontend Deployment (Vercel)
1. Connect your GitHub repository to Vercel
2. Set environment variables in Vercel dashboard:
   ```
   NEXT_PUBLIC_API_URL=https://your-api-domain.com/api
   ```
3. Deploy automatically on push to main branch

### Backend Deployment (Railway/Heroku)
1. Create a new project on your hosting platform
2. Set environment variables:
   ```
   MONGODB_URI=mongodb+srv://...
   JWT_SECRET=your-production-secret
   NODE_ENV=production
   PORT=5000
   ```
3. Deploy the API directory
4. Update frontend environment variables with production API URL

### Database Deployment
- Use MongoDB Atlas for cloud database
- Update connection string in environment variables
- Set up proper database indexes for performance

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name**
- GitHub: [@root-775](https://github.com/root-775)
- Email: webdeveloper.amitgupta@gmail.com

## 🙏 Acknowledgments

- Next.js team for the amazing React framework
- Express.js for the robust backend framework
- MongoDB for the flexible database solution
- Tailwind CSS for the utility-first CSS framework
- All open-source contributors who made this project possible

---

**Happy Blogging! 🎉**
