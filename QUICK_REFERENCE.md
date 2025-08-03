# Quick Reference - Online CV Theme

## Essential Configuration

### Site Setup (_config.yml)
```yaml
title: "Your Name - Title"
url: "https://yourdomain.com"
baseurl: "/repo-name"
description: "Brief description"
theme_skin: blue|turquoise|green|berry|orange|ceramic
analytics: "UA-XXXXXXX-X"
```

### Basic Profile (_data/data.yml)
```yaml
sidebar:
  name: "Your Name"
  tagline: "Your Title"
  avatar: "profile.jpg"
  email: "your@email.com"
  phone: "+1 234 567 8900"
  website: "yoursite.com"
  linkedin: "username"
  github: "username"
  
career-profile:
  title: "Career Profile"
  summary: "Your professional summary here"
```

## Component Files

| Component | File | Purpose |
|-----------|------|---------|
| Site Head | `_includes/head.html` | Meta tags, CSS, favicon |
| Sidebar | `_includes/sidebar.html` | Profile and navigation |
| Contact | `_includes/contact.html` | Social media links |
| Career | `_includes/career-profile.html` | Professional summary |
| Experience | `_includes/experiences.html` | Work history |
| Education | `_includes/education.html` | Academic background |
| Skills | `_includes/skills.html` | Technical skills |
| Projects | `_includes/projects.html` | Portfolio projects |
| Publications | `_includes/publications.html` | Papers and articles |
| Languages | `_includes/language.html` | Language proficiency |
| Interests | `_includes/interests.html` | Personal interests |
| Scripts | `_includes/scripts.html` | JavaScript includes |
| Footer | `_includes/footer.html` | Page footer |

## Data Schemas

### Experience Entry
```yaml
- role: "Job Title"
  time: "2020 - Present"
  company: "Company Name"
  details: "Description with **markdown** support"
```

### Education Entry
```yaml
- degree: "Degree Name"
  university: "Institution"
  time: "2018 - 2020"
  details: "Optional details"
```

### Project Entry
```yaml
- title: "Project Name"
  link: "https://github.com/user/repo"
  tagline: "Brief description"
```

### Skill Entry
```yaml
- name: "Technology Name"
  level: "85%"
```

### Language Entry
```yaml
- idiom: "Language Name"
  level: "Native|Professional|Conversational|Basic"
```

### Interest Entry
```yaml
- item: "Interest Name"
  link: "https://optional-link.com"
```

## SASS Mixins

### Shadows
```scss
@include text-shadow($string);
@include box-shadow($string);
@include drop-shadow($x, $y, $blur, $spread, $alpha);
```

### Borders
```scss
@include border-radius($radius);
@include border-radiuses($tr, $br, $bl, $tl);
```

### Transforms
```scss
@include transform($string);
@include scale($factor);
@include rotate($deg);
@include translate($x, $y);
```

### Transitions
```scss
@include transition($duration, $ease);
@include transition-duration($duration);
```

## CSS Classes

### Layout
- `.wrapper` - Main container
- `.sidebar-wrapper` - Sidebar container
- `.main-wrapper` - Content area
- `.section` - Content section

### Profile
- `.profile-container` - Profile area
- `.avatar` - Profile image
- `.name` - Profile name
- `.tagline` - Profile tagline

### Skills
- `.level-bar` - Skill container
- `.level-bar-inner` - Skill indicator
- `.level-title` - Skill name

### General
- `.section-title` - Section headings
- `.item` - Generic content item
- `.intro` - Introduction text

## Liquid Template Variables

### Site Variables
```liquid
{{ site.title }}
{{ site.baseurl }}
{{ site.description }}
{{ site.analytics }}
```

### Data Variables
```liquid
{{ site.data.data.sidebar.name }}
{{ site.data.data.sidebar.email }}
{{ site.data.data.career-profile.summary }}
{{ site.data.data.experiences }}
{{ site.data.data.skills.toolset }}
```

### Loops
```liquid
{% for experience in site.data.data.experiences %}
  {{ experience.role }}
{% endfor %}

{% for skill in site.data.data.skills.toolset %}
  {{ skill.name }} - {{ skill.level }}
{% endfor %}
```

## Jekyll Commands

```bash
# Development
bundle exec jekyll serve
bundle exec jekyll serve --livereload

# Production build
JEKYLL_ENV=production bundle exec jekyll build

# With incremental builds
bundle exec jekyll serve --incremental

# Profile performance
bundle exec jekyll build --profile
```

## Color Themes

### Available Skins
- `blue` (default)
- `turquoise`
- `green`
- `berry`
- `orange`
- `ceramic`

### Theme Variables
```scss
$theme-color         // Primary color
$text-color          // Main text
$text-color-secondary // Secondary text
$sidebar-bg          // Sidebar background
$link-color          // Links
$link-hover-color    // Link hover
```

## Custom Component Template

### 1. Create Include
```html
<!-- _includes/custom-section.html -->
{% assign data = site.data.data.custom-section %}
{% if data %}
<section class="section custom-section">
  <h2 class="section-title">
    <span class="fa-stack fa-xs">
      <i class="fas fa-circle fa-stack-2x"></i>
      <i class="fas fa-icon fa-stack-1x fa-inverse"></i>
    </span>
    {{ data.title }}
  </h2>
  
  {% for item in data.items %}
  <div class="item">
    <h3>{{ item.title }}</h3>
    <p>{{ item.content }}</p>
  </div>
  {% endfor %}
</section>
{% endif %}
```

### 2. Add Data
```yaml
# _data/data.yml
custom-section:
  title: "Section Title"
  items:
    - title: "Item 1"
      content: "Content 1"
```

### 3. Include in Layout
```html
<!-- index.html -->
{% include custom-section.html %}
```

## Responsive Breakpoints

```scss
// Phone
@media (max-width: 767px) { }

// Tablet  
@media (min-width: 768px) and (max-width: 991px) { }

// Desktop
@media (min-width: 992px) { }

// Large Desktop
@media (min-width: 1200px) { }
```

## Social Platform URLs

| Platform | URL Pattern |
|----------|-------------|
| LinkedIn | `https://linkedin.com/in/{{ username }}` |
| GitHub | `https://github.com/{{ username }}` |
| Twitter | `https://twitter.com/{{ username }}` |
| Stack Overflow | `https://stackoverflow.com/users/{{ id/username }}` |
| GitLab | `https://gitlab.com/{{ username }}` |
| Bitbucket | `https://bitbucket.com/{{ username }}` |
| CodeWars | `https://codewars.com/users/{{ username }}` |
| Goodreads | `https://goodreads.com/user/show/{{ id-username }}` |

## Common Troubleshooting

### Styles Not Loading
1. Check `baseurl` in `_config.yml`
2. Restart Jekyll server after config changes
3. Clear browser cache

### Images Not Showing
1. Verify file exists in `/assets/images/`
2. Check filename matches `avatar` value
3. Ensure correct file permissions

### Social Links Broken
1. Use username only (not full URL)
2. Check platform-specific format requirements
3. Verify icon classes are correct

### Build Errors
```bash
# Check YAML syntax
ruby -e "require 'yaml'; YAML.load_file('_data/data.yml')"

# Verbose build output
bundle exec jekyll build --verbose

# Check for missing dependencies
bundle install
```

## File Structure

```
/
├── _config.yml           # Site configuration
├── _data/
│   └── data.yml         # Main data file
├── _includes/           # Reusable components
├── _layouts/            # Page templates
├── _sass/               # Stylesheets
│   ├── _base.scss
│   ├── _mixins.scss
│   └── skins/           # Color themes
├── assets/
│   ├── css/
│   ├── images/          # Profile photo here
│   └── js/
└── index.html           # Main page
```

---

**Pro Tips:**
- Always restart Jekyll after `_config.yml` changes
- Use `{% raw %}{% endraw %}` for literal Liquid syntax
- Test responsive design with browser dev tools
- Optimize images for web (WebP format recommended)
- Use `--livereload` for auto-refresh during development