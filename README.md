# 🔄 Micro.blog Redirector Theme

A minimal, robust Hugo theme for [Micro.blog](https://micro.blog) focused on private notes with smart redirects and clean presentation. Built for reliability with comprehensive fallback handling and parameterized configuration.

## 📋 Summary

This theme is designed for Micro.blog sites that need:

- **🔒 Private Notes with Redirects**: Automatic redirection for non-note content with fallback links
- **📸 Photo Grid Display**: Responsive photo galleries with lazy loading
- **🎧 Podcast Support**: Full iTunes-compatible podcast feeds with metadata
- **📰 Multiple Feed Formats**: JSON Feed, RSS, and specialized content feeds
- **🌐 IndieWeb Integration**: Microformats, webmentions, and social syndication
- **⚡ Modern Styling**: Clean, responsive design with Inter font and new.css framework
- **🛡️ Robust Error Handling**: Defensive parameter checking and graceful degradation

## 🚀 How to Use

### Installation

1. **Clone this theme** to your Hugo site's themes directory:
   ```bash
   git clone https://github.com/harperreed/mb-redirector-theme.git themes/mb-redirector
   ```

2. **Configure your site** by updating your `config.json` with your details:
   ```json
   {
     "title": "Your Site Title",
     "author": {
       "name": "Your Full Name",
       "username": "yourusername",
       "avatar": "https://your-avatar-url.com/image.jpg"
     },
     "baseURL": "https://yoursite.com/",
     "params": {
       "default_redirect_url": "https://yoursite.com/notes/",
       "copyright_name": "Your Full Name",
       "hosting_provider": "Micro.blog",
       "hosting_url": "https://micro.blog",
       "header_avatar": "https://your-avatar-url.com/image.jpg",
       "navigation_links": [
         {"text": "Your Blog", "url": "https://yourblog.com"},
         {"text": "Another Site", "url": "https://yoursite.com"},
         {"text": "Email", "url": "mailto:you@email.com"}
       ]
     }
   }
   ```

### Theme-Specific Parameters

All personal data is configurable through `config.json` parameters:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `default_redirect_url` | URL to redirect non-note pages | `{baseURL}notes/` |
| `copyright_name` | Name in footer copyright | `.Site.Author.name` |
| `hosting_provider` | Hosting service name | `"Micro.blog"` |
| `hosting_url` | Hosting service URL | `"https://micro.blog"` |
| `header_avatar` | Avatar image in header | `.Site.Author.avatar` |
| `navigation_links` | Array of navigation link objects | `[]` |

### Content Types

#### 📝 Regular Posts
Standard blog posts with optional titles, categories, and full content.

#### 🔒 Private Notes
Create private notes by setting:
- `Type: "note"`
- `Section: "notes"`

These will render with the full page layout. All other content will automatically redirect to your configured `default_redirect_url`.

#### 🔗 Redirect Pages
Create redirect pages using the `redirect` layout type:
```yaml
---
type: redirect
redirect: "https://destination-url.com"
---
```

If the `redirect` parameter is missing, the page will show a friendly error message instead of breaking.

#### 📷 Photo Posts
Add photos to any post with:
```yaml
photos:
  - "https://your-image-url.jpg"
  - "https://another-image.jpg"
```

#### 🎧 Podcast Episodes
For podcast episodes, include:
```yaml
audio_with_metadata:
  - url: "https://your-podcast-file.mp3"
    size: 12345678
    duration_seconds: 1800
```

### Feed Formats Available

- **RSS Feed**: `/feed.xml`
- **JSON Feed**: `/feed.json` 
- **Photos Feed**: `/photos/index.json`
- **Archive Feed**: `/archive/index.json`
- **Podcast Feed**: `/podcast.xml` and `/podcast.json`

## 🛠️ Tech Info

### Built With

- **Hugo**: Static site generator
- **Go Templates**: Theme templating system
- **new.css**: Minimal CSS framework
- **Inter Font**: Modern typography via fonts.xz.style
- **Microformats**: h-feed, h-entry markup for IndieWeb

### Key Features

#### 🎨 Styling & Layout
- Responsive CSS Grid for photo galleries
- Clean, modern typography with Inter font
- Dark theme support for shared notes
- Mobile-optimized responsive design

#### 🔌 Integrations
- **Micro.blog**: Native integration with posting, editing, and syndication
- **ActivityPub**: Built-in ActivityPub support for federation
- **IndieAuth**: Authentication endpoint support
- **Webmentions**: Full webmention receiving capability
- **Bluesky**: Social syndication support

#### 📊 Content Management
- Automatic sitemap generation
- Multiple taxonomy support (categories)
- Custom RSS with markdown source
- RSD (Really Simple Discovery) support
- Newsletter email template

#### 🔄 Robustness Features
- **Smart Redirects**: Meta refresh with clickable fallback links for accessibility
- **Defensive Coding**: All parameters validated with sensible defaults
- **Error Handling**: Graceful degradation when configuration is missing
- **No Hardcoded Data**: Everything configurable through `config.json`
- **Portable**: Can be reused across sites with zero code changes
- **Standards Compliant**: Proper HTML5 DOCTYPEs and semantic markup
- **Plugin System**: CSS/JS/HTML extension support
- **Theme Versioning**: Cache busting support

### File Structure
```
layouts/
├── _default/           # Base templates
├── partials/          # Reusable components  
├── redirect/          # Redirect page template
└── [format].html/json # Specialized output formats
```

### Configuration Options

The theme supports extensive customization through `config.json`:

- **Navigation**: Custom navigation links with flexible text/URL structure
- **Social**: Twitter, GitHub, Instagram integration via rel="me" links
- **Podcast**: iTunes metadata and feeds (XML + JSON)
- **Hosting**: Custom hosting provider attribution in footer
- **Styling**: Plugin CSS/JS injection system
- **Feeds**: Custom feed endpoints and formats
- **Redirects**: Configurable default redirect URL
- **Branding**: Custom avatars, copyright names, and site identity

### Design Philosophy

This theme prioritizes **robustness** and **portability**:

1. **No Hardcoded Values**: All personal data lives in `config.json`
2. **Defensive Defaults**: Every parameter has a sensible fallback
3. **Fail Gracefully**: Missing configuration shows helpful errors, not broken pages
4. **Accessibility First**: Redirect pages include manual links for when meta refresh fails
5. **Standards Compliant**: Proper HTML5, microformats, and IndieWeb support

### License

MIT License - feel free to fork, modify, and use for your own projects! 🎉

---

*Built with ❤️ for the IndieWeb community by [@harperreed](https://github.com/harperreed)*
