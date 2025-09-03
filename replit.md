# CyberSec Research Hub

## Overview

CyberSec Research Hub is a full-stack web application designed as an interactive platform for cybersecurity research, threat intelligence, and educational content. The application serves as a comprehensive hub where users can explore cybersecurity research papers, methodologies, latest news, and tutorials. It features a modern React frontend with a Node.js/Express backend, utilizing PostgreSQL for data persistence and supporting PDF document uploads for research papers.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
The frontend is built using React with TypeScript and follows a component-based architecture. Key architectural decisions include:

- **UI Framework**: Utilizes shadcn/ui components built on top of Radix UI primitives for consistent, accessible interface elements
- **Styling**: Tailwind CSS with a dark theme design system and custom CSS variables for theming
- **State Management**: React Query (@tanstack/react-query) for server state management, providing caching, synchronization, and background updates
- **Routing**: Wouter for lightweight client-side routing
- **Form Handling**: React Hook Form with Zod schema validation for type-safe form management
- **Build Tool**: Vite for fast development and optimized production builds

### Backend Architecture  
The backend follows a RESTful API design pattern with Express.js:

- **Framework**: Express.js with TypeScript for type safety
- **API Design**: RESTful endpoints under `/api` namespace with proper HTTP status codes and error handling
- **File Handling**: Multer middleware for PDF file uploads with validation and storage management
- **Logging**: Custom request/response logging middleware for API monitoring
- **Error Handling**: Centralized error handling middleware with proper status codes

### Data Storage Solutions
The application uses a hybrid approach for data persistence:

- **Database**: PostgreSQL as the primary database, configured through Drizzle ORM for type-safe database operations
- **Schema Management**: Drizzle Kit for database migrations and schema management
- **Connection**: Neon Database serverless PostgreSQL for cloud-native deployment
- **Development Storage**: In-memory storage implementation for development/testing purposes
- **File Storage**: Local file system storage for uploaded PDF documents with organized directory structure

### Database Schema Design
The schema includes two main entities:

- **Users**: Simple authentication system with username/password
- **Blog Posts**: Comprehensive content management with fields for title, content, excerpt, category (research/methods/news/tutorials), tags, featured images, PDF attachments, and timestamps
- **File Metadata**: PDF path and size tracking for document management

### Authentication and Authorization
Currently implements a basic foundation for user management:

- User creation and retrieval by ID or username
- Password storage (note: production implementation would require proper hashing)
- Session management preparation with connect-pg-simple for PostgreSQL session store

### API Structure
RESTful API design with the following endpoints:

- `GET /api/blog-posts` - Retrieve all posts with optional category and search filtering
- `GET /api/blog-posts/:id` - Retrieve specific post by ID
- `POST /api/blog-posts` - Create new post with optional PDF upload
- `PUT /api/blog-posts/:id` - Update existing post
- `DELETE /api/blog-posts/:id` - Delete post
- Search functionality integrated into the main posts endpoint

### Content Management Features
- **Category System**: Four content types (research, methods, news, tutorials) with distinct styling
- **Search Functionality**: Full-text search across post titles and content
- **PDF Integration**: Upload, store, and view PDF research papers with metadata tracking
- **Rich Content**: Support for featured images, tags, read time estimation, and excerpts

## External Dependencies

### Core Framework Dependencies
- **React 18**: Frontend framework with modern hooks and concurrent features
- **Express.js**: Backend web framework for Node.js
- **TypeScript**: Type safety across the entire application stack
- **Vite**: Build tool and development server with fast HMR

### Database and ORM
- **Drizzle ORM**: Type-safe database toolkit with PostgreSQL support
- **@neondatabase/serverless**: Serverless PostgreSQL database connection
- **Drizzle Kit**: Database migration and schema management tool

### UI and Styling
- **Tailwind CSS**: Utility-first CSS framework for rapid UI development
- **Radix UI**: Unstyled, accessible UI primitives for complex components
- **shadcn/ui**: Pre-built component library based on Radix UI
- **Lucide React**: Icon library for consistent iconography
- **class-variance-authority**: Utility for creating variant-based component APIs

### Form and Data Handling
- **React Hook Form**: Performant forms with minimal re-renders
- **@hookform/resolvers**: Integration with validation libraries
- **Zod**: TypeScript-first schema validation
- **@tanstack/react-query**: Server state management with caching and synchronization

### File Upload and Processing
- **Multer**: Middleware for handling multipart/form-data and file uploads
- **File System API**: Node.js built-in module for file operations

### Development and Deployment
- **@replit/vite-plugin-runtime-error-modal**: Development error overlay
- **@replit/vite-plugin-cartographer**: Replit-specific development tools
- **ESBuild**: Fast bundler for production builds
- **TSX**: TypeScript execution for development server

### Utility Libraries
- **clsx & tailwind-merge**: Conditional CSS class handling
- **date-fns**: Date manipulation and formatting
- **nanoid**: Unique ID generation
- **wouter**: Lightweight routing library for React