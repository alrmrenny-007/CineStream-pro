CineStream Pro
A free, browser-based streaming discovery platform that allows users to browse, search, and stream thousands of movies and TV series. Built with vanilla HTML/JavaScript and powered by Supabase authentication, TMDB metadata, and multiple embedded streaming sources.
 
Features
 	Google OAuth and email/password authentication via Supabase
 	Browse trending movies, popular series, top-rated titles, and now-playing content
Filter content by genre for both movies and TV series
Full-text search across movies and series
Multiple streaming server sources (VidSrc, 2Embed,
MultiEmbed, EmbedSu, MoviesAPI, VidLink)
TV series season and episode selector
Download links via YTS and EZTV torrent indexes
Responsive hero banner with featured daily trending content
User account menu with sign-out functionality
Session-protected main app — unauthenticated users are redirected to the login page
Tech Stack
Layer	Technology
Frontend	HTML5, CSS3, Vanilla JavaScript
Authentication	Supabase Auth (Google OAuth 2.0,
Email/Password)
Movie
Metadata	TMDB API (The Movie Database)
Streaming	VidSrc, 2Embed, MultiEmbed,
EmbedSu, MoviesAPI, VidLink
Hosting	Render (Static Site)
Local Dev	VS Code + Live Server
 
Project Structure
 
Authentication Flow
1.	User lands on CineStream-Auth.html
2.	Signs in via Google OAuth or email/password through Supabase
3.	On successful authentication, Supabase fires an onAuthStateChange event
4.	The auth page redirects the user to CineStream-
Pro.html
5.	The app page calls db.auth.getSession() on load — if no session is found, the user is redirected back to the auth page
 
Setup & Local Development
Prerequisites
VS Code with the Live Server extension
A Supabase project
A TMDB API key (free at themoviedb.org)
A Google Cloud project with OAuth 2.0 credentials
1. Clone the repository
 
2. Configure Supabase
 
Replace these with your own values from Supabase → Settings → API.
3. Configure Google OAuth
 	Enable Google as a provider in Supabase →
Authentication → Providers
Add your Google OAuth Client ID and Client Secret
Register https://YOUR_PROJECT.supabase.co/auth/v1/callback
as an Authorized Redirect URI in Google Cloud Console Add your local dev origin (e.g.
http://localhost:5500 ) to Authorized JavaScript Origins
4. Set Supabase Redirect URLs
In Supabase → Authentication → URL Configuration:
Site URL: http://localhost:5500
Redirect URLs: http://localhost:5500/CineStream-
Auth.html
5. Lock Live Server port
 
6. Run
Right-click CineStream-Auth.html in VS Code → Open with Live Server
 
Deployment (Render)
1.	Push the repository to GitHub
2.	Go to render.com → New → Static Site
3.	Connect your GitHub repository
4.	Set Publish Directory to .
5.	Deploy
6.	Once live, update all redirect URLs in Supabase and Google Cloud Console to your Render domain (e.g. https://cinestream-pro.onrender.com )
Environment Notes
 	The TMDB API key is entered by the user at runtime via an in-app banner and stored in localStorage
 	Supabase credentials are hardcoded in the HTML files
— do not expose the service_role key; only the anon public key is used
This project is intended for personal/educational use
Data Sources
 	Movie and series metadata: The Movie Database (TMDB)
 
License
This project is for personal and educational use only. All movie data is provided by TMDB. Streaming content is served via third-party embed sources.
