# Discord Bot Dashboard - Replit.md

## Overview
This is a full-stack web application for managing a Discord bot called "WTJ Envoy". The application provides a dashboard interface for configuring bot settings, monitoring activity, and viewing statistics. The system uses a modern React frontend with a Node.js/Express backend, PostgreSQL database with Drizzle ORM, and Discord.js for bot functionality.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Styling**: Tailwind CSS with custom Discord-themed colors
- **UI Components**: Radix UI components via shadcn/ui
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **Build Tool**: Vite with custom configuration

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL
- **Discord Integration**: Discord.js v14
- **API Design**: RESTful endpoints with JSON responses
- **Error Handling**: Centralized error middleware

### Data Storage Architecture
- **Primary Database**: PostgreSQL (via Neon Database)
- **ORM**: Drizzle ORM with TypeScript schema definitions
- **Fallback Storage**: In-memory storage for development/testing
- **Session Storage**: PostgreSQL sessions with connect-pg-simple

## Key Components

### Database Schema
The application uses four main tables:
- **users**: Basic user authentication (username/password)
- **bot_config**: Discord bot configuration (channel IDs, role IDs, messages)
- **activity_logs**: Bot activity tracking (welcomes, restarts, errors)
- **bot_stats**: Performance metrics (uptime, message counts, server counts)

### Discord Bot Service
- **Event Handling**: Guild member updates, role changes
- **Welcome System**: Automated staff member welcoming
- **Activity Logging**: Tracks all bot actions and events
- **Status Monitoring**: Real-time connection and uptime tracking

### Frontend Components
- **Dashboard**: Main overview with stats and recent activity
- **Bot Configuration**: Channel and role ID management
- **Activity Logs**: Real-time bot activity monitoring
- **Welcome Message Template**: Customizable welcome message editor
- **Sidebar Navigation**: Discord-themed navigation interface

### API Endpoints
- `GET/PUT /api/config`: Bot configuration management
- `GET/POST /api/logs`: Activity log retrieval and creation
- `GET/PUT /api/stats`: Bot statistics tracking
- `GET /api/bot/status`: Real-time bot connection status
- `POST /api/bot/restart`: Bot restart functionality
- `POST /api/bot/stop`: Bot shutdown functionality

## Data Flow

1. **Configuration Flow**: Frontend → API → Database → Discord Bot
2. **Activity Monitoring**: Discord Events → Bot Service → Database → API → Frontend
3. **Statistics Updates**: Bot Service → Database → API → Frontend (polling)
4. **User Actions**: Frontend → API → Bot Service → Discord API

## External Dependencies

### Database
- **Neon Database**: Serverless PostgreSQL hosting
- **Connection**: Via `@neondatabase/serverless` driver
- **Migrations**: Managed through Drizzle Kit

### Discord Integration
- **Discord.js v14**: Official Discord API library
- **Required Intents**: Guilds, GuildMembers, GuildMessages, MessageContent
- **Bot Permissions**: Manage roles, send messages, read message history

### UI Framework
- **shadcn/ui**: Pre-built accessible components
- **Radix UI**: Headless UI primitives
- **Tailwind CSS**: Utility-first styling
- **Lucide React**: Icon library

### Development Tools
- **Vite**: Fast build tool and dev server
- **TypeScript**: Type safety across the stack
- **Replit Integration**: Runtime error overlay and cartographer

## Deployment Strategy

### Production Build
1. Frontend builds to `dist/public` via Vite
2. Backend compiles to `dist/index.js` via esbuild
3. Single Node.js process serves both frontend and API

### Environment Configuration
- **DATABASE_URL**: PostgreSQL connection string (required)
- **DISCORD_TOKEN**: Bot authentication token
- **NODE_ENV**: Environment specification (development/production)

### Process Management
- **Development**: Uses tsx for hot reloading
- **Production**: Direct Node.js execution
- **Database**: Automatic migrations via Drizzle

### Hosting Considerations
- Requires persistent storage for database
- Needs environment variables for Discord token
- Bot requires 24/7 uptime for Discord event handling

## Changelog
- July 02, 2025. Initial setup

## User Preferences
Preferred communication style: Simple, everyday language.