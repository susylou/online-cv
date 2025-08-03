# Online CV Theme - Comprehensive Documentation

## Table of Contents

1. [Overview](#overview)
2. [Installation & Setup](#installation--setup)
3. [Configuration API](#configuration-api)
4. [Data Structure API](#data-structure-api)
5. [Layout Components](#layout-components)
6. [Include Components](#include-components)
7. [Styling System](#styling-system)
8. [Theme Customization](#theme-customization)
9. [Usage Examples](#usage-examples)
10. [Troubleshooting](#troubleshooting)

## Overview

The Online CV Theme is a responsive Jekyll-based website template designed for creating professional resumes and portfolios. It features a modular component architecture with data-driven content management.

### Key Features
- **Responsive Design**: Mobile-first approach with Bootstrap framework
- **Modular Components**: Reusable include files for each section
- **Data-Driven**: Centralized configuration via YAML data files
- **Theme Variations**: 6 different color schemes
- **Social Integration**: Support for multiple social platforms
- **Print-Friendly**: Optimized CSS for printing

## Installation & Setup

### Prerequisites
- Jekyll 3.0+
- Ruby 2.4+
- Git

### Quick Start

```bash
# Fork and clone the repository
git clone https://github.com/yourusername/online-cv.git
cd online-cv

# Install dependencies
bundle install

# Start development server
bundle exec jekyll serve

# View at http://localhost:4000
```

### GitHub Pages Deployment

1. Fork the repository
2. Enable GitHub Pages in repository settings
3. Set source branch to `main` or `gh-pages`
4. Access at `https://yourusername.github.io/online-cv/`

## Configuration API

### Site Configuration (`_config.yml`)

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `title` | String | "My Resume" | Site title displayed in browser tab |
| `url` | String | - | Base URL for the site |
| `baseurl` | String | "/online-cv" | Subpath where site is served |
| `description` | String | - | Meta description for SEO |
| `theme_skin` | String | "blue" | Color scheme (blue, turquoise, green, berry, orange, ceramic) |
| `chrome_mobile_color` | String | - | Chrome mobile address bar color (hex format) |
| `analytics` | String | - | Google Analytics tracking ID |

#### Example Configuration

```yaml
title: John Doe - Software Engineer
url: 'https://johndoe.github.io'
baseurl: '/my-cv'
description: Senior Software Engineer specializing in full-stack development
theme_skin: turquoise
chrome_mobile_color: '#2E8B57'
analytics: UA-123456789-1
```

## Data Structure API

### Main Data File (`_data/data.yml`)

The primary configuration is managed through a single YAML file with the following structure:

#### Sidebar Configuration

```yaml
sidebar:
  about: true              # Show/hide about section
  education: true          # Show education in sidebar (false = main section)
  
  # Profile Information
  name: "Your Name"
  tagline: "Your Professional Title"
  avatar: "profile.png"    # Image file in /assets/images/
  
  # Contact Information
  email: "your.email@domain.com"
  phone: "+1 234 567 8900"
  website: "yourwebsite.com"        # Without http://
  linkedin: "linkedin-username"
  github: "github-username"
  gitlab: "gitlab-username"
  bitbucket: "bitbucket-username"
  twitter: "@twitter-handle"
  stack-overflow: "123456/username"  # ID/Username format
  codewars: "codewars-username"
  goodreads: "123456-username"      # ID-Username format
```

#### Languages Section

```yaml
languages:
  - idiom: "English"
    level: "Native"
  - idiom: "Spanish"
    level: "Professional"
```

**Parameters:**
- `idiom` (String): Language name
- `level` (String): Proficiency level (Native, Professional, Conversational, Basic)

#### Interests Section

```yaml
interests:
  - item: "Photography"
    link: "https://optional-link.com"
  - item: "Hiking"
    link: ""  # Empty for no link
```

**Parameters:**
- `item` (String, Required): Interest/hobby name
- `link` (String, Optional): External link related to the interest

#### Career Profile Section

```yaml
career-profile:
  title: "Career Profile"
  summary: |
    Multi-line career summary using YAML literal syntax.
    Supports markdown formatting including [links](url).
    
    Multiple paragraphs are supported.
```

**Parameters:**
- `title` (String): Section heading
- `summary` (String): Career description supporting markdown

#### Education Section

```yaml
education:
  - degree: "Master of Science in Computer Science"
    university: "Stanford University"
    time: "2018 - 2020"
    details: |
      Detailed description of studies and achievements.
      
      - Bullet point 1
      - Bullet point 2
```

**Parameters:**
- `degree` (String): Degree title
- `university` (String): Institution name
- `time` (String): Duration/timeframe
- `details` (String): Description with markdown support

#### Experience Section

```yaml
experiences:
  - role: "Senior Software Engineer"
    time: "2020 - Present"
    company: "Tech Company Inc."
    details: |
      Role description and key achievements.
      
      - Achievement 1
      - Achievement 2
```

**Parameters:**
- `role` (String): Job title
- `time` (String): Employment duration
- `company` (String): Company name
- `details` (String): Role description with markdown support

#### Projects Section

```yaml
projects:
  title: "Projects"
  intro: "Optional introduction to your projects section."
  
  assignments:
    - title: "Project Name"
      link: "https://project-url.com"
      tagline: "Brief project description"
```

**Parameters:**
- `title` (String): Section heading
- `intro` (String, Optional): Section introduction
- `assignments` (Array): List of projects
  - `title` (String): Project name
  - `link` (String): Project URL or "#" for placeholder
  - `tagline` (String): Brief description

#### Publications Section

```yaml
publications:
  title: "Publications"
  intro: "Optional introduction text."
  
  papers:
    - title: "Paper Title"
      authors: "Author Names"
      conference: "Conference/Journal Name, Year"
```

**Parameters:**
- `title` (String): Section heading
- `intro` (String, Optional): Section introduction
- `papers` (Array): List of publications
  - `title` (String): Publication title
  - `authors` (String): Author names
  - `conference` (String): Publication venue and year

#### Skills Section

```yaml
skills:
  title: "Skills & Proficiency"
  
  toolset:
    - name: "Python & Django"
      level: "98%"
    - name: "JavaScript & React"
      level: "85%"
```

**Parameters:**
- `title` (String): Section heading
- `toolset` (Array): List of skills
  - `name` (String): Skill/technology name
  - `level` (String): Proficiency percentage (0-100%)

#### Footer Configuration

```yaml
footer: >
  Custom footer text with <i class="fas fa-heart"></i> icons
  and <a href="url">links</a> supported.
```

## Layout Components

### Default Layout (`_layouts/default.html`)

The main page template structure:

```html
<!DOCTYPE html>
<html lang="en">
  {% include head.html %}
  <body>
    <div class="wrapper">
      {% include sidebar.html %}
      <div class="main-wrapper">
        {{ content }}
      </div>
    </div>
    {% include footer.html %}
    {% include scripts.html %}
  </body>
</html>
```

**Usage:**
```yaml
---
layout: default
---
Page content goes here
```

### Compress Layout (`_layouts/compress.html`)

Minifies HTML output for production:

```yaml
---
layout: compress
---
```

## Include Components

### Head Component (`_includes/head.html`)

Manages meta tags, CSS, and page metadata.

**Features:**
- Responsive viewport configuration
- SEO-optimized meta tags
- Theme color support for mobile browsers
- Bootstrap and Font Awesome integration
- Conditional IE support

**Customization:**
```html
<!-- Custom meta tags -->
<meta name="author" content="Your Name">
<meta name="keywords" content="keyword1, keyword2">
```

### Sidebar Component (`_includes/sidebar.html`)

Main navigation and profile section.

**Structure:**
```html
<div class="sidebar-wrapper">
  <div class="profile-container">
    <!-- Avatar, name, tagline -->
  </div>
  {% include contact.html %}
  {% if sidebar.education %}{% include education.html %}{% endif %}
  {% include language.html %}
  {% include interests.html %}
  {% if sidebar.about %}{% include about.html %}{% endif %}
</div>
```

**Conditional Rendering:**
- Education section can be moved to main content
- About section can be hidden
- All sections respect data availability

### Contact Component (`_includes/contact.html`)

Social media and contact information display.

**Supported Platforms:**
- Email (with mailto: links)
- Phone (with tel: links)
- Website
- LinkedIn
- GitHub
- GitLab
- Bitbucket
- Twitter
- Stack Overflow
- CodeWars
- Goodreads

**Custom Platform Addition:**
```html
{% if sidebar.custom-platform %}
<li class="custom-platform">
  <i class="fab fa-custom-icon"></i>
  <a href="https://platform.com/{{ sidebar.custom-platform }}" target="_blank">
    {{ sidebar.custom-platform }}
  </a>
</li>
{% endif %}
```

### Content Sections

#### Career Profile (`_includes/career-profile.html`)
Displays professional summary from `career-profile` data.

#### Education (`_includes/education.html`)
Renders education history with conditional sidebar/main placement.

#### Experience (`_includes/experiences.html`)
Lists work experience with company, role, and achievements.

#### Projects (`_includes/projects.html`)
Showcases projects with links and descriptions.

#### Publications (`_includes/publications.html`)
Academic/professional publications list.

#### Skills (`_includes/skills.html`)
Visual skill proficiency bars with percentage indicators.

#### Languages (`_includes/language.html`)
Language proficiency sidebar widget.

#### Interests (`_includes/interests.html`)
Personal interests/hobbies with optional links.

### Utility Components

#### Analytics (`_includes/analytics.html`)
Google Analytics integration when `analytics` is configured.

#### Scripts (`_includes/scripts.html`)
JavaScript loading and initialization.

#### Footer (`_includes/footer.html`)
Page footer with customizable content.

## Styling System

### SASS Architecture

```
_sass/
├── _base.scss       # Base styles and resets
├── _default.scss    # Default theme colors
├── _mixins.scss     # Reusable style mixins
├── _print.scss      # Print-specific styles
├── _responsive.scss # Media queries
└── skins/           # Color theme variations
    ├── _blue.scss
    ├── _turquoise.scss
    ├── _green.scss
    ├── _berry.scss
    ├── _orange.scss
    └── _ceramic.scss
```

### Available Mixins

#### Shadow Mixins

```scss
@include text-shadow($string: 0 1px 3px rgba(0, 0, 0, 0.25));
@include box-shadow($string);
@include drop-shadow($x: 0, $y: 1px, $blur: 2px, $spread: 0, $alpha: 0.25);
@include inner-shadow($x: 0, $y: 1px, $blur: 2px, $spread: 0, $alpha: 0.25);
```

#### Border Mixins

```scss
@include border-radius($radius: 5px);
@include border-radiuses($topright: 0, $bottomright: 0, $bottomleft: 0, $topleft: 0);
```

#### Layout Mixins

```scss
@include box-sizing($type: border-box);
@include opacity($opacity: 0.5);
```

#### Gradient Mixins

```scss
@include gradient($startColor: #eee, $endColor: white);
@include horizontal-gradient($startColor: #eee, $endColor: white);
@include vertical-gradient($startColor: #eee, $endColor: white);
```

#### Transform Mixins

```scss
@include transform($string);
@include scale($factor);
@include rotate($deg);
@include skew($deg, $deg2);
@include translate($x, $y);
@include translate3d($x, $y, $z);
```

#### Animation Mixins

```scss
@include transition($duration: 0.2s, $ease: ease-out);
@include transition-duration($duration: 0.2s);
@include animation-duration($duration: 0.2s);
```

### Responsive Breakpoints

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

### Custom CSS Classes

#### Layout Classes
- `.wrapper`: Main page container
- `.sidebar-wrapper`: Sidebar container
- `.main-wrapper`: Main content area
- `.section`: Content section wrapper

#### Component Classes
- `.profile-container`: Profile information area
- `.contact-list`: Contact information list
- `.section-title`: Section headings
- `.item`: Generic item container

#### Utility Classes
- `.level-bar`: Skill level indicator
- `.level-bar-inner`: Skill level fill
- `.fa-stack`: Font Awesome icon stacking

## Theme Customization

### Creating a Custom Color Scheme

1. Create a new skin file: `_sass/skins/_custom.scss`

```scss
/* Custom Theme Colors */
$theme-color: #your-primary-color;
$text-color: #your-text-color;
$text-color-secondary: #your-secondary-color;
$text-muted: #your-muted-color;
$divider: #your-divider-color;
$lighter-gray: #your-light-gray;
$darker-gray: #your-dark-gray;
$sidebar-bg: #your-sidebar-bg;
$link-color: #your-link-color;
$link-hover-color: #your-link-hover-color;
```

2. Update `_config.yml`:

```yaml
theme_skin: custom
```

### Adding Custom Sections

1. Create include file: `_includes/custom-section.html`

```html
{% assign custom_data = site.data.data.custom-section %}
{% if custom_data %}
<section class="section custom-section">
  <h2 class="section-title">
    <span class="fa-stack fa-xs">
      <i class="fas fa-circle fa-stack-2x"></i>
      <i class="fas fa-custom-icon fa-stack-1x fa-inverse"></i>
    </span>
    {{ custom_data.title }}
  </h2>
  
  <!-- Custom content rendering -->
  {% for item in custom_data.items %}
    <div class="item">
      <h3>{{ item.title }}</h3>
      <p>{{ item.description }}</p>
    </div>
  {% endfor %}
</section>
{% endif %}
```

2. Add data structure to `_data/data.yml`:

```yaml
custom-section:
  title: "Custom Section"
  items:
    - title: "Item 1"
      description: "Description 1"
    - title: "Item 2"
      description: "Description 2"
```

3. Include in `index.html`:

```html
{% include custom-section.html %}
```

### Modifying Existing Components

#### Adding New Social Platform

1. Update `_data/data.yml`:

```yaml
sidebar:
  discord: "username#1234"
```

2. Modify `_includes/contact.html`:

```html
{% if sidebar.discord %}
<li class="discord"><i class="fab fa-discord"></i>
  <a href="https://discord.com/users/{{ sidebar.discord }}" target="_blank">{{ sidebar.discord }}</a>
</li>
{% endif %}
```

#### Customizing Skill Display

Replace percentage bars with custom indicators:

```html
<!-- In _includes/skills.html -->
{% for skill in skills.toolset %}
<div class="item">
  <h3 class="level-title">{{ skill.name }}</h3>
  <div class="level-bar">
    <div class="level-bar-inner" data-level="{{ skill.level }}">
      <!-- Custom content -->
      <span class="skill-rating">
        {% assign rating = skill.level | remove: '%' | plus: 0 | divided_by: 20 %}
        {% for i in (1..5) %}
          {% if i <= rating %}⭐{% else %}☆{% endif %}
        {% endfor %}
      </span>
    </div>
  </div>
</div>
{% endfor %}
```

## Usage Examples

### Basic Setup

1. **Configure your information:**

```yaml
# _data/data.yml
sidebar:
  name: "Jane Smith"
  tagline: "Full Stack Developer"
  avatar: "profile.jpg"
  email: "jane@example.com"
  github: "janesmith"
  linkedin: "jane-smith"

career-profile:
  title: "Career Profile"
  summary: |
    Experienced developer with 5+ years in web development.
    Passionate about creating scalable applications.
```

2. **Add your photo:**
Place `profile.jpg` in `/assets/images/`

3. **Customize theme:**
```yaml
# _config.yml
title: Jane Smith - Developer Portfolio
theme_skin: green
```

### Advanced Customization

#### Multi-language Setup

```yaml
languages:
  - idiom: "English"
    level: "Native"
  - idiom: "Spanish"
    level: "Professional"
  - idiom: "French"
    level: "Conversational"
```

#### Comprehensive Experience Section

```yaml
experiences:
  - role: "Senior Full Stack Developer"
    time: "2020 - Present"
    company: "TechCorp Solutions"
    details: |
      Leading development of microservices architecture serving 1M+ users.
      
      Key achievements:
      - Reduced API response time by 40%
      - Implemented automated testing pipeline
      - Mentored 3 junior developers
      - Led migration to cloud infrastructure
      
      **Technologies:** React, Node.js, AWS, Docker, Kubernetes
```

#### Rich Projects Portfolio

```yaml
projects:
  title: "Featured Projects"
  intro: "Selection of personal and professional projects showcasing my technical expertise."
  
  assignments:
    - title: "E-commerce Platform"
      link: "https://github.com/user/ecommerce"
      tagline: "Full-stack e-commerce solution built with React and Node.js. Features include user authentication, payment processing, and admin dashboard."
    
    - title: "Mobile Weather App"
      link: "https://apps.apple.com/app/weather"
      tagline: "Cross-platform mobile app using React Native. Integrates with multiple weather APIs and features location-based forecasts."
```

### Performance Optimization

#### Optimize Images

```bash
# Compress profile image
imageoptim assets/images/profile.png

# Or use ImageMagick
convert profile.jpg -resize 100x100^ -gravity center -extent 100x100 profile-optimized.jpg
```

#### Enable Compression

```yaml
# _config.yml
compress-site: yes
compress_html:
  clippings: all
  ignore:
    envs: development
```

#### Lazy Loading Implementation

```html
<!-- In _includes/head.html -->
<style>
  .lazy-image {
    opacity: 0;
    transition: opacity 0.3s;
  }
  .lazy-image.loaded {
    opacity: 1;
  }
</style>

<!-- In _includes/scripts.html -->
<script>
  // Lazy loading implementation
  const images = document.querySelectorAll('.lazy-image');
  const imageObserver = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        img.classList.add('loaded');
        observer.unobserve(img);
      }
    });
  });
  
  images.forEach(img => imageObserver.observe(img));
</script>
```

## Troubleshooting

### Common Issues

#### 1. Site Not Loading Correctly

**Problem:** Styles not loading or broken layout
**Solution:**
- Check `baseurl` in `_config.yml` matches your deployment path
- Ensure all asset paths are relative to `site.baseurl`
- Verify Jekyll serve is running without errors

#### 2. Images Not Displaying

**Problem:** Profile image or other images not showing
**Solution:**
```yaml
# Correct image path in _data/data.yml
sidebar:
  avatar: "profile.png"  # File must exist in /assets/images/profile.png
```

#### 3. Social Links Not Working

**Problem:** Social media links broken or incorrectly formatted
**Solution:**
```yaml
# Correct format examples
sidebar:
  linkedin: "username"           # NOT the full URL
  github: "username"            # NOT the full URL
  twitter: "@username"          # Include @ symbol
  stack-overflow: "123/username" # Use ID/username format
```

#### 4. Theme Color Not Changing

**Problem:** Color scheme not updating
**Solution:**
- Restart Jekyll server after changing `theme_skin`
- Verify skin name matches available options
- Clear browser cache

#### 5. Print Styles Issues

**Problem:** Resume doesn't print correctly
**Solution:**
- Check `_sass/_print.scss` for print-specific styles
- Test print preview in browser
- Adjust CSS for better print layout

### Development Tips

#### Local Development

```bash
# Development with live reload
bundle exec jekyll serve --livereload

# Development with incremental builds
bundle exec jekyll serve --incremental

# Build for production
JEKYLL_ENV=production bundle exec jekyll build
```

#### Debugging Liquid Templates

```html
<!-- Add debug output -->
{{ variable | inspect }}

<!-- Check if variable exists -->
{% if variable %}
  Variable exists: {{ variable }}
{% else %}
  Variable is empty or undefined
{% endif %}
```

#### Validating YAML

```bash
# Check YAML syntax
ruby -e "require 'yaml'; YAML.load_file('_data/data.yml')"

# Or use online YAML validator
# https://yamlchecker.com/
```

### Performance Monitoring

#### Lighthouse Audit

```bash
# Install Lighthouse CLI
npm install -g lighthouse

# Run audit
lighthouse http://localhost:4000 --output html --output-path ./audit-report.html
```

#### Jekyll Build Performance

```bash
# Profile build time
bundle exec jekyll build --profile

# Verbose output
bundle exec jekyll build --verbose
```

### SEO Optimization

#### Meta Tags Enhancement

```html
<!-- In _includes/head.html -->
<meta name="author" content="{{ site.data.data.sidebar.name }}">
<meta name="robots" content="index, follow">
<meta property="og:title" content="{{ site.title }}">
<meta property="og:description" content="{{ site.description }}">
<meta property="og:image" content="{{ site.url }}{{ site.baseurl }}/assets/images/{{ site.data.data.sidebar.avatar }}">
<meta property="og:url" content="{{ site.url }}{{ site.baseurl }}">
<meta name="twitter:card" content="summary">
```

#### Structured Data

```html
<!-- Add JSON-LD structured data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Person",
  "name": "{{ site.data.data.sidebar.name }}",
  "jobTitle": "{{ site.data.data.sidebar.tagline }}",
  "email": "{{ site.data.data.sidebar.email }}",
  "url": "{{ site.url }}{{ site.baseurl }}"
}
</script>
```

---

This documentation provides comprehensive coverage of all public APIs, components, and customization options available in the Online CV Jekyll theme. For additional support or advanced customizations, refer to the Jekyll documentation and the theme's GitHub repository.