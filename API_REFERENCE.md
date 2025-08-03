# API Reference - Online CV Theme

## Overview

This document provides detailed API specifications for all public interfaces, functions, and components in the Online CV Jekyll theme.

## Configuration APIs

### Jekyll Site Configuration

#### `_config.yml` Parameters

```yaml
# Core Configuration
title: String                    # Site title
url: String                      # Production URL
baseurl: String                  # Site subpath
description: String              # Meta description

# Theme Configuration  
theme_skin: Enum                 # Color scheme selector
chrome_mobile_color: String      # Mobile browser color (hex)

# Analytics
analytics: String                # Google Analytics ID

# Build Settings
compress-site: Boolean           # Enable HTML compression
port: Integer                    # Development server port
host: String                     # Development server host
safe: Boolean                    # Safe mode flag
```

**Supported `theme_skin` Values:**
- `blue` (default)
- `turquoise`
- `green` 
- `berry`
- `orange`
- `ceramic`

### Data Configuration API

#### `_data/data.yml` Schema

```yaml
# Root Schema
sidebar: SidebarConfig           # Sidebar configuration
career-profile: CareerProfile    # Professional summary
education: Education[]           # Education history
experiences: Experience[]        # Work experience
projects: Projects               # Project portfolio
publications: Publications      # Academic/professional publications
skills: Skills                   # Technical skills
footer: String                   # Footer content (HTML supported)
```

#### SidebarConfig Schema

```yaml
# Display Controls
about: Boolean                   # Show about section
education: Boolean               # Show education in sidebar

# Profile Information
name: String                     # Full name
tagline: String                  # Professional title
avatar: String                   # Image filename (in /assets/images/)

# Contact Information
email: String                    # Email address
phone: String                    # Phone number
website: String                  # Website URL (without protocol)

# Social Media (all optional)
linkedin: String                 # LinkedIn username
github: String                   # GitHub username
gitlab: String                   # GitLab username
bitbucket: String                # Bitbucket username
twitter: String                  # Twitter handle (with @)
stack-overflow: String           # Format: "ID/username"
codewars: String                 # CodeWars username
goodreads: String                # Format: "ID-username"

# Sidebar Sections
languages: Language[]            # Language proficiency
interests: Interest[]            # Personal interests
```

#### Language Schema

```yaml
idiom: String                    # Language name
level: Enum                      # Proficiency level
```

**Supported `level` Values:**
- `Native`
- `Professional` 
- `Conversational`
- `Basic`

#### Interest Schema

```yaml
item: String                     # Interest/hobby name
link: String?                    # Optional external link
```

#### CareerProfile Schema

```yaml
title: String                    # Section heading
summary: String                  # Multi-line summary (Markdown supported)
```

#### Education Schema (Array)

```yaml
degree: String                   # Degree title
university: String               # Institution name
time: String                     # Time period
details: String?                 # Optional details (Markdown supported)
```

#### Experience Schema (Array)

```yaml
role: String                     # Job title
time: String                     # Employment period
company: String                  # Company name
details: String?                 # Optional role description (Markdown supported)
```

#### Projects Schema

```yaml
title: String                    # Section heading
intro: String?                   # Optional introduction
assignments: Assignment[]        # Project list
```

#### Assignment Schema

```yaml
title: String                    # Project name
link: String                     # Project URL or "#"
tagline: String                  # Brief description
```

#### Publications Schema

```yaml
title: String                    # Section heading
intro: String?                   # Optional introduction
papers: Paper[]                  # Publication list
```

#### Paper Schema

```yaml
title: String                    # Publication title
authors: String                  # Author names
conference: String               # Publication venue
```

#### Skills Schema

```yaml
title: String                    # Section heading
toolset: Skill[]                 # Skills list
```

#### Skill Schema

```yaml
name: String                     # Skill/technology name
level: String                    # Proficiency percentage (e.g., "85%")
```

## Layout APIs

### Default Layout

**File:** `_layouts/default.html`

**Usage:**
```yaml
---
layout: default
---
```

**Template Variables:**
- `{{ content }}` - Page content
- `{{ site.*}}` - Site configuration variables
- `{{ site.data.data.*}}` - Data file variables

### Compress Layout

**File:** `_layouts/compress.html`

**Usage:**
```yaml
---
layout: compress
---
```

**Purpose:** Minifies HTML output for production builds.

## Component APIs

### Include Components

All include components follow the pattern `{% include component-name.html %}`.

#### Head Component
**File:** `_includes/head.html`

**Purpose:** HTML head section with meta tags, CSS, and favicons.

**Dependencies:**
- Site configuration variables
- Bootstrap CSS
- Font Awesome icons

#### Sidebar Component
**File:** `_includes/sidebar.html`

**Purpose:** Left sidebar with profile and navigation.

**Data Dependencies:**
```liquid
{{ site.data.data.sidebar }}
```

**Conditional Includes:**
- `contact.html` (always included)
- `education.html` (if `sidebar.education` is true)
- `language.html` (always included)
- `interests.html` (always included)
- `about.html` (if `sidebar.about` is true)

#### Contact Component
**File:** `_includes/contact.html`

**Purpose:** Contact information and social media links.

**Data Source:**
```liquid
{{ site.data.data.sidebar }}
```

**Supported Fields:**
- `email` → `mailto:` link
- `phone` → `tel:` link
- `website` → External link (adds http://)
- `linkedin` → LinkedIn profile
- `github` → GitHub profile
- `gitlab` → GitLab profile
- `bitbucket` → Bitbucket profile
- `twitter` → Twitter profile
- `stack-overflow` → Stack Overflow profile
- `codewars` → CodeWars profile
- `goodreads` → Goodreads profile

#### Content Section Components

##### Career Profile
**File:** `_includes/career-profile.html`

**Data Source:**
```liquid
{{ site.data.data.career-profile }}
```

**Template Structure:**
```html
<section class="section summary-section">
  <h2 class="section-title">{{ career-profile.title }}</h2>
  <div class="summary">{{ career-profile.summary | markdownify }}</div>
</section>
```

##### Education
**File:** `_includes/education.html`

**Data Source:**
```liquid
{{ site.data.data.education }}
```

**Conditional Rendering:**
- Renders in sidebar if `site.data.data.sidebar.education` is true
- Renders in main content if `site.data.data.sidebar.education` is false

##### Experience
**File:** `_includes/experiences.html`

**Data Source:**
```liquid
{{ site.data.data.experiences }}
```

**Loop Structure:**
```liquid
{% for experience in experiences %}
  <!-- Render experience item -->
{% endfor %}
```

##### Projects
**File:** `_includes/projects.html`

**Data Source:**
```liquid
{{ site.data.data.projects }}
```

**Template Structure:**
```html
<section class="section projects-section">
  <h2 class="section-title">{{ projects.title }}</h2>
  <div class="intro">{{ projects.intro }}</div>
  {% for project in projects.assignments %}
    <!-- Render project item -->
  {% endfor %}
</section>
```

##### Publications
**File:** `_includes/publications.html`

**Data Source:**
```liquid
{{ site.data.data.publications }}
```

##### Skills
**File:** `_includes/skills.html`

**Data Source:**
```liquid
{{ site.data.data.skills }}
```

**Visual Elements:**
- Progress bars with percentage indicators
- Icon integration

##### Languages
**File:** `_includes/language.html`

**Data Source:**
```liquid
{{ site.data.data.sidebar.languages }}
```

##### Interests
**File:** `_includes/interests.html`

**Data Source:**
```liquid
{{ site.data.data.sidebar.interests }}
```

#### Utility Components

##### Analytics
**File:** `_includes/analytics.html`

**Trigger Condition:**
```liquid
{% if site.analytics %}
```

**Integration:** Google Analytics tracking code.

##### Scripts
**File:** `_includes/scripts.html`

**Purpose:** JavaScript loading and initialization.

##### Footer
**File:** `_includes/footer.html`

**Data Source:**
```liquid
{{ site.data.data.footer }}
```

## SASS APIs

### Mixin Library
**File:** `_sass/_mixins.scss`

#### Shadow Mixins

```scss
@mixin text-shadow($string: 0 1px 3px rgba(0, 0, 0, 0.25))
@mixin box-shadow($string)
@mixin drop-shadow($x: 0, $y: 1px, $blur: 2px, $spread: 0, $alpha: 0.25)
@mixin inner-shadow($x: 0, $y: 1px, $blur: 2px, $spread: 0, $alpha: 0.25)
```

#### Border Mixins

```scss
@mixin border-radius($radius: 5px)
@mixin border-radiuses($topright: 0, $bottomright: 0, $bottomleft: 0, $topleft: 0)
```

#### Transform Mixins

```scss
@mixin transform($string)
@mixin scale($factor)
@mixin rotate($deg)
@mixin skew($deg, $deg2)
@mixin translate($x, $y)
@mixin translate3d($x, $y, $z)
```

#### Transition Mixins

```scss
@mixin transition($duration: 0.2s, $ease: ease-out)
@mixin transition-duration($duration: 0.2s)
@mixin animation-duration($duration: 0.2s)
```

#### Gradient Mixins

```scss
@mixin gradient($startColor: #eee, $endColor: white)
@mixin horizontal-gradient($startColor: #eee, $endColor: white)
@mixin vertical-gradient($startColor: #eee, $endColor: white)
@mixin radial-gradient($startColor: #eee, $endColor: white)
```

#### Layout Mixins

```scss
@mixin box-sizing($type: border-box)
@mixin opacity($opacity: 0.5)
@mixin center-block()
@mixin clearfix()
```

#### Typography Mixins

```scss
@mixin font-size($size: 1.6, $line: $size * 1.25)
@mixin font-rem($size)
@mixin font-family($family: $font-family-sans-serif)
```

### Color Theme API

#### Theme Structure
**Location:** `_sass/skins/`

**Files:**
- `_blue.scss` (default)
- `_turquoise.scss`
- `_green.scss`
- `_berry.scss`
- `_orange.scss`
- `_ceramic.scss`

#### Color Variables

```scss
$theme-color: #color;              // Primary theme color
$text-color: #color;               // Main text color
$text-color-secondary: #color;     // Secondary text color
$text-muted: #color;               // Muted text color
$divider: #color;                  // Divider/border color
$lighter-gray: #color;             // Light gray background
$darker-gray: #color;              // Dark gray background
$sidebar-bg: #color;               // Sidebar background
$link-color: #color;               // Link color
$link-hover-color: #color;         // Link hover color
```

#### Creating Custom Themes

1. Create new skin file: `_sass/skins/_name.scss`
2. Define color variables
3. Update `_config.yml`: `theme_skin: name`

### CSS Class APIs

#### Layout Classes

```css
.wrapper                   /* Main page container */
.sidebar-wrapper          /* Sidebar container */
.main-wrapper             /* Main content area */
.section                  /* Content section wrapper */
.container-block          /* Generic container */
```

#### Profile Classes

```css
.profile-container        /* Profile information area */
.avatar                   /* Profile image */
.name                     /* Profile name */
.tagline                  /* Profile tagline */
```

#### Contact Classes

```css
.contact-container        /* Contact section wrapper */
.contact-list             /* Contact list container */
.email                    /* Email contact item */
.phone                    /* Phone contact item */
.website                  /* Website contact item */
.linkedin                 /* LinkedIn contact item */
.github                   /* GitHub contact item */
/* Additional social platform classes follow same pattern */
```

#### Content Classes

```css
.section-title            /* Section headings */
.section-title .fa-stack  /* Icon stack for section titles */
.intro                    /* Section introduction text */
.item                     /* Generic content item */
.summary                  /* Career profile summary */
```

#### Skills Classes

```css
.level-title              /* Skill name */
.level-bar                /* Skill level container */
.level-bar-inner          /* Skill level indicator */
```

#### Responsive Classes

```css
.visible-xs               /* Visible on extra small screens only */
.visible-sm               /* Visible on small screens only */
.visible-md               /* Visible on medium screens only */
.visible-lg               /* Visible on large screens only */
.hidden-xs                /* Hidden on extra small screens */
.hidden-sm                /* Hidden on small screens */
.hidden-md                /* Hidden on medium screens */
.hidden-lg                /* Hidden on large screens */
```

## Extension APIs

### Custom Component Creation

#### Step 1: Create Include File

**File:** `_includes/custom-section.html`

```html
{% assign section_data = site.data.data.custom-section %}
{% if section_data %}
<section class="section custom-section">
  <h2 class="section-title">
    <span class="fa-stack fa-xs">
      <i class="fas fa-circle fa-stack-2x"></i>
      <i class="fas fa-custom-icon fa-stack-1x fa-inverse"></i>
    </span>
    {{ section_data.title }}
  </h2>
  
  {% if section_data.intro %}
  <div class="intro">{{ section_data.intro }}</div>
  {% endif %}
  
  {% for item in section_data.items %}
  <div class="item">
    <h3 class="item-title">{{ item.title }}</h3>
    <div class="item-content">{{ item.content | markdownify }}</div>
  </div>
  {% endfor %}
</section>
{% endif %}
```

#### Step 2: Add Data Schema

**File:** `_data/data.yml`

```yaml
custom-section:
  title: "Section Title"
  intro: "Optional introduction text"
  items:
    - title: "Item Title"
      content: "Item content with **markdown** support"
```

#### Step 3: Include in Layout

**File:** `index.html`

```html
{% include custom-section.html %}
```

### Custom Social Platform Integration

#### Implementation Pattern

```html
{% if sidebar.platform-name %}
<li class="platform-name">
  <i class="fab fa-platform-icon"></i>
  <a href="https://platform.com/{{ sidebar.platform-name }}" target="_blank">
    {{ sidebar.platform-name }}
  </a>
</li>
{% endif %}
```

#### Required Steps

1. Add platform field to `_data/data.yml`
2. Add HTML snippet to `_includes/contact.html`
3. Add CSS styles for `.platform-name` class
4. Ensure Font Awesome icon is available

### JavaScript API

#### Available Events

```javascript
// Document ready
document.addEventListener('DOMContentLoaded', function() {
  // Custom initialization code
});

// Window load
window.addEventListener('load', function() {
  // Post-load initialization
});
```

#### Accessing Data

```javascript
// Site configuration
const siteData = {
  title: "{{ site.title }}",
  baseurl: "{{ site.baseurl }}",
  // Add other site variables as needed
};

// User data
const userData = {
  name: "{{ site.data.data.sidebar.name }}",
  email: "{{ site.data.data.sidebar.email }}",
  // Add other user data as needed
};
```

## Build APIs

### Jekyll Commands

```bash
# Development server
bundle exec jekyll serve

# Production build
JEKYLL_ENV=production bundle exec jekyll build

# With specific config
bundle exec jekyll serve --config _config.yml,_config_dev.yml

# Profile build performance
bundle exec jekyll build --profile

# Incremental builds
bundle exec jekyll serve --incremental
```

### Environment Variables

```bash
JEKYLL_ENV=production          # Production environment
JEKYLL_LOG_LEVEL=debug        # Debug logging
```

### Custom Build Scripts

#### Deployment Script

```bash
#!/bin/bash
# deploy.sh

echo "Building site..."
JEKYLL_ENV=production bundle exec jekyll build

echo "Optimizing assets..."
# Add asset optimization commands

echo "Deploying to server..."
# Add deployment commands
```

#### Development Script

```bash
#!/bin/bash
# dev.sh

echo "Starting development server..."
bundle exec jekyll serve --livereload --incremental
```

---

This API reference provides complete specifications for all programmatic interfaces in the Online CV theme. Use this document for development, customization, and integration purposes.