# Pictura - Instagram Clone

A full-stack social media application built with Next.js and Supabase, featuring real-time messaging, stories, notifications, and more.

![Pictura](https://placeholder.svg?height=400&width=800&query=Pictura%20Instagram%20Clone%20Social%20Media%20App)

## Features

- **Authentication** - Email/password login and registration with automatic profile creation
- **User Profiles** - Customizable profiles with avatar, bio, name, and username
- **Posts** - Create posts with images and captions, like and comment on posts
- **Stories** - 24-hour expiring stories with image or text content
- **Real-time Messaging** - Direct messages with real-time updates
- **Notifications** - Get notified on likes, comments, and follows
- **Explore** - Discover new content and search for users
- **Dark Mode** - Toggle between light, dark, and system themes
- **Private Accounts** - Make your profile private to control who sees your posts

## Tech Stack

- **Frontend**: Next.js 15, React 19, Tailwind CSS 4, shadcn/ui
- **Backend**: Supabase (PostgreSQL, Auth, Storage, Realtime)
- **State Management**: SWR for data fetching and caching

## Prerequisites

- Node.js 18+ 
- A Supabase account and project
- npm or yarn or pnpm

## Getting Started

### 1. Clone the repository

\`\`\`bash
git clone https://github.com/yourusername/pictura.git
cd pictura
\`\`\`

### 2. Install dependencies

\`\`\`bash
npm install
# or
yarn install
# or
pnpm install
\`\`\`

### 3. Set up environment variables

Create a `.env.local` file in the root directory:

\`\`\`env
# Supabase
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key

# For development email redirects
NEXT_PUBLIC_DEV_SUPABASE_REDIRECT_URL=http://localhost:3000
\`\`\`

### 4. Set up the database

Run the SQL scripts in the `scripts` folder in order:

1. **Create tables** - `001_create_tables.sql`
   - Creates all necessary tables: profiles, posts, likes, comments, stories, conversations, messages, follows

2. **Create profile trigger** - `002_create_profile_trigger.sql`
   - Automatically creates a profile when a user signs up

3. **Enable realtime** - `003_enable_realtime.sql`
   - Enables real-time subscriptions for messages and notifications

4. **Create storage bucket** - `004_create_storage_bucket.sql`
   - Creates the media storage bucket for images

5. **Storage policies** - `005_storage_policies.sql`
   - Sets up storage policies for file uploads

6. **Add private account** - `006_add_private_account.sql`
   - Adds the private account feature

7. **Create notifications** - `007_create_notifications.sql`
   - Creates the notifications table with real-time support

You can run these scripts via:
- Supabase Dashboard SQL Editor
- Supabase CLI: `supabase db push`

### 5. Run the development server

\`\`\`bash
npm run dev
# or
yarn dev
# or
pnpm dev
\`\`\`

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

\`\`\`
├── app/
│   ├── (main)/              # Protected routes with app shell
│   │   ├── feed/            # Home feed
│   │   ├── explore/         # Discover content
│   │   ├── create/          # Create new post
│   │   ├── messages/        # Direct messages
│   │   ├── notifications/   # Notifications
│   │   ├── profile/         # User profiles
│   │   ├── post/            # Individual post view
│   │   ├── settings/        # App settings
│   │   └── stories/         # Create stories
│   ├── auth/                # Authentication pages
│   └── layout.tsx           # Root layout
├── components/
│   ├── explore/             # Explore page components
│   ├── feed/                # Feed components
│   ├── layout/              # App shell and navigation
│   ├── messages/            # Messaging components
│   ├── notifications/       # Notification components
│   ├── post/                # Post-related components
│   ├── profile/             # Profile components
│   ├── providers/           # Context providers
│   ├── settings/            # Settings components
│   ├── stories/             # Stories components
│   └── ui/                  # shadcn/ui components
├── hooks/                   # Custom React hooks
├── lib/
│   ├── supabase/            # Supabase client utilities
│   ├── notifications.ts     # Notification helpers
│   └── types.ts             # TypeScript types
└── scripts/                 # Database setup scripts
\`\`\`

## Database Schema

### Tables

| Table | Description |
|-------|-------------|
| `profiles` | User profiles with avatar, bio, username |
| `posts` | User posts with images and captions |
| `likes` | Post likes |
| `comments` | Post comments |
| `stories` | 24-hour stories |
| `follows` | User follow relationships |
| `conversations` | Message conversations |
| `messages` | Direct messages |
| `notifications` | User notifications |

## Features in Detail

### Authentication
- Email/password authentication via Supabase Auth
- Automatic profile creation on signup
- Protected routes with middleware

### Posts
- Upload images with captions
- Like and comment on posts
- Edit and delete your own posts
- View individual post details

### Stories
- Create image or text-based stories
- Stories auto-expire after 24 hours
- Full-screen story viewer with progress bars
- Navigate between multiple stories

### Messaging
- Real-time direct messages
- Conversation list with last message preview
- Start new conversations from any profile

### Notifications
- Real-time notification updates
- Notifications for likes, comments, and follows
- Unread count badge
- Mark all as read

### Privacy
- Private account option
- Only followers can see private account posts
- Follow requests for private accounts

## Deployment

### Deploy to Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/yourusername/pictura)

1. Push your code to GitHub
2. Import the project to Vercel
3. Add environment variables
4. Deploy

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Next.js](https://nextjs.org/)
- [Supabase](https://supabase.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Lucide Icons](https://lucide.dev/)
