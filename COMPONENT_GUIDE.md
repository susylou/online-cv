# Component Usage Guide - Online CV Theme

## Overview

This guide provides practical examples and best practices for using and customizing all components in the Online CV Jekyll theme.

## Quick Start Components

### Basic Profile Setup

```yaml
# _data/data.yml - Minimal required configuration
sidebar:
  name: "Your Name"
  tagline: "Your Professional Title"
  avatar: "profile.jpg"  # Place in /assets/images/
  email: "your@email.com"
  
career-profile:
  title: "Career Profile"
  summary: |
    Brief professional summary highlighting your key skills and experience.
```

### Essential Sections

```yaml
# Skills section with visual progress bars
skills:
  title: "Skills & Proficiency"
  toolset:
    - name: "Python"
      level: "90%"
    - name: "JavaScript"
      level: "85%"
    - name: "React"
      level: "80%"

# Experience section
experiences:
  - role: "Software Engineer"
    time: "2020 - Present"
    company: "Tech Company"
    details: |
      Key responsibilities and achievements:
      - Built scalable web applications
      - Led team of 3 developers
      - Improved performance by 40%
```

## Sidebar Components

### Contact Information Component

**File**: `_includes/contact.html`

**Complete Example**:
```yaml
# _data/data.yml
sidebar:
  # Basic contact
  email: "john.doe@example.com"
  phone: "+1 (555) 123-4567"
  website: "johndoe.dev"  # Without http://
  
  # Social platforms
  linkedin: "john-doe-dev"
  github: "johndoe"
  twitter: "@johndoe_dev"
  stack-overflow: "123456/john-doe"
  
  # Optional platforms
  gitlab: "johndoe"
  bitbucket: "johndoe"
  codewars: "johndoe"
  goodreads: "123456-john-doe"
```

**Output**: Renders as clickable icons with proper links:
- Email: `mailto:` links
- Phone: `tel:` links for mobile dialing
- Social: Direct profile links

**Customization Example**:
```html
<!-- Add custom platform to _includes/contact.html -->
{% if sidebar.discord %}
<li class="discord">
  <i class="fab fa-discord"></i>
  <a href="https://discord.com/users/{{ sidebar.discord }}" target="_blank">
    {{ sidebar.discord }}
  </a>
</li>
{% endif %}
```

### Languages Component

**File**: `_includes/language.html`

**Usage Example**:
```yaml
# _data/data.yml
sidebar:
  languages:
    - idiom: "English"
      level: "Native"
    - idiom: "Spanish"
      level: "Professional"
    - idiom: "French"
      level: "Conversational"
    - idiom: "German"
      level: "Basic"
```

**Styling**: Automatically renders with appropriate visual indicators.

### Interests Component

**File**: `_includes/interests.html`

**Basic Example**:
```yaml
# _data/data.yml
sidebar:
  interests:
    - item: "Photography"
      link: "https://instagram.com/yourphotos"
    - item: "Hiking"
      link: ""  # No link
    - item: "Open Source"
      link: "https://github.com/yourusername"
```

**Advanced Example with Categories**:
```yaml
sidebar:
  interests:
    - item: "Machine Learning"
      link: "https://kaggle.com/yourusername"
    - item: "Technical Writing"
      link: "https://medium.com/@yourusername"
    - item: "Rock Climbing"
      link: ""
    - item: "Cooking"
      link: "https://yourfoodblog.com"
```

## Main Content Components

### Career Profile Component

**File**: `_includes/career-profile.html`

**Basic Example**:
```yaml
# _data/data.yml
career-profile:
  title: "Career Profile"
  summary: |
    Experienced full-stack developer with 5+ years building scalable web applications.
    Passionate about clean code, user experience, and continuous learning.
```

**Advanced Example with Markdown**:
```yaml
career-profile:
  title: "Professional Summary"
  summary: |
    **Senior Software Engineer** with expertise in modern web technologies:
    
    - **Frontend**: React, Vue.js, TypeScript, CSS3/HTML5
    - **Backend**: Node.js, Python, PostgreSQL, MongoDB
    - **DevOps**: Docker, AWS, CI/CD pipelines
    
    Led development teams and delivered [award-winning applications](https://example.com)
    serving 100K+ users. Committed to writing maintainable code and mentoring
    junior developers.
    
    Currently exploring machine learning applications in web development.
```

### Experience Component

**File**: `_includes/experiences.html`

**Comprehensive Example**:
```yaml
# _data/data.yml
experiences:
  - role: "Senior Full Stack Developer"
    time: "Jan 2021 - Present"
    company: "TechCorp Inc., San Francisco"
    details: |
      **Leading a team of 5 developers** in building next-generation e-commerce platform.
      
      **Key Achievements:**
      - Architected microservices handling 1M+ daily transactions
      - Reduced page load times by 60% through optimization
      - Implemented automated testing reducing bugs by 80%
      - Mentored 3 junior developers who were promoted
      
      **Technologies:** React, Node.js, AWS, Docker, PostgreSQL, Redis
      
      **Notable Projects:**
      - Payment processing system (PCI compliance)
      - Real-time inventory management dashboard
      - Mobile app with offline capabilities

  - role: "Frontend Developer"
    time: "Mar 2019 - Dec 2020"
    company: "StartupXYZ, Remote"
    details: |
      **Developed responsive web applications** for B2B SaaS platform.
      
      - Built component library used across 10+ applications
      - Implemented accessibility features (WCAG 2.1 AA compliance)
      - Collaborated with UX team on design system
      
      **Technologies:** Vue.js, TypeScript, SCSS, Jest, Storybook

  - role: "Junior Web Developer"
    time: "Jun 2018 - Feb 2019"
    company: "Digital Agency, New York"
    details: |
      **Frontend development** for client websites and web applications.
      
      - Delivered 15+ client projects on time and budget
      - Learned modern development practices and agile methodology
      
      **Technologies:** JavaScript, PHP, WordPress, Bootstrap
```

### Projects Component

**File**: `_includes/projects.html`

**Portfolio Example**:
```yaml
# _data/data.yml
projects:
  title: "Featured Projects"
  intro: >
    Selection of personal and professional projects that showcase my
    technical skills and problem-solving abilities.

  assignments:
    - title: "TaskFlow - Project Management App"
      link: "https://github.com/yourusername/taskflow"
      tagline: "Full-stack web application built with React and Node.js. Features real-time collaboration, file uploads, and team management. Deployed on AWS with CI/CD pipeline."

    - title: "WeatherAI - ML Weather Prediction"
      link: "https://github.com/yourusername/weatherai"
      tagline: "Machine learning model predicting weather patterns using TensorFlow. Includes REST API and React dashboard. Achieved 92% accuracy on test data."

    - title: "CryptoTracker - Investment Portfolio"
      link: "https://cryptotracker-demo.netlify.app"
      tagline: "Cryptocurrency portfolio tracker with real-time price updates. Built with Vue.js and integrated with multiple exchange APIs. Mobile-responsive design."

    - title: "BlogCMS - Content Management System"
      link: "https://github.com/yourusername/blogcms"
      tagline: "Headless CMS built with Node.js and GraphQL. Features user authentication, rich text editing, and SEO optimization. Used by 500+ bloggers."

    - title: "SmartHome IoT Dashboard"
      link: "#"
      tagline: "IoT dashboard for home automation using Raspberry Pi and Python. Controls lighting, temperature, and security systems. Real-time monitoring and alerts."
```

### Skills Component

**File**: `_includes/skills.html`

**Comprehensive Skills Example**:
```yaml
# _data/data.yml
skills:
  title: "Technical Skills"
  toolset:
    # Programming Languages
    - name: "JavaScript & TypeScript"
      level: "95%"
    - name: "Python"
      level: "90%"
    - name: "Java"
      level: "75%"
    - name: "Go"
      level: "60%"
    
    # Frontend Technologies
    - name: "React & Redux"
      level: "95%"
    - name: "Vue.js & Vuex"
      level: "85%"
    - name: "HTML5 & CSS3/SCSS"
      level: "95%"
    - name: "Webpack & Vite"
      level: "80%"
    
    # Backend Technologies
    - name: "Node.js & Express"
      level: "90%"
    - name: "Django & FastAPI"
      level: "85%"
    - name: "PostgreSQL & MongoDB"
      level: "85%"
    - name: "Redis & Elasticsearch"
      level: "70%"
    
    # DevOps & Tools
    - name: "Docker & Kubernetes"
      level: "80%"
    - name: "AWS & GCP"
      level: "75%"
    - name: "Git & CI/CD"
      level: "90%"
    - name: "Linux & Bash"
      level: "85%"
```

**Alternative Skills Display** (Custom):
```html
<!-- Custom skills template -->
{% assign skills = site.data.data.skills %}
{% if skills %}
<section class="section skills-section">
  <h2 class="section-title">{{ skills.title }}</h2>
  
  <div class="skills-grid">
    {% for category in skills.categories %}
    <div class="skill-category">
      <h3>{{ category.name }}</h3>
      <div class="skill-tags">
        {% for skill in category.items %}
        <span class="skill-tag level-{{ skill.level }}">
          {{ skill.name }}
        </span>
        {% endfor %}
      </div>
    </div>
    {% endfor %}
  </div>
</section>
{% endif %}
```

### Education Component

**File**: `_includes/education.html`

**Academic Example**:
```yaml
# _data/data.yml
education:
  - degree: "Master of Science in Computer Science"
    university: "Stanford University"
    time: "2016 - 2018"
    details: |
      **Specialization:** Machine Learning and Artificial Intelligence
      
      **Coursework:**
      - Advanced Algorithms and Data Structures
      - Machine Learning Theory and Applications
      - Distributed Systems and Cloud Computing
      - Software Engineering Principles
      
      **Thesis:** "Deep Learning Applications in Natural Language Processing"
      **GPA:** 3.8/4.0

  - degree: "Bachelor of Science in Software Engineering"
    university: "University of California, Berkeley"
    time: "2012 - 2016"
    details: |
      **Magna Cum Laude** graduate with focus on web technologies.
      
      **Relevant Projects:**
      - Senior Capstone: E-learning platform (team of 6)
      - Database Systems: Library management system
      - Software Architecture: Microservices application
      
      **Activities:**
      - President, Computer Science Student Association
      - Teaching Assistant for Data Structures course
      - Volunteer coding instructor for local nonprofits
```

**Professional Certifications Example**:
```yaml
education:
  - degree: "AWS Certified Solutions Architect"
    university: "Amazon Web Services"
    time: "2023"
    details: |
      Professional-level certification demonstrating expertise in:
      - Designing distributed applications on AWS
      - Security and compliance best practices
      - Cost optimization strategies

  - degree: "Certified Kubernetes Administrator"
    university: "Cloud Native Computing Foundation"
    time: "2022"
    details: |
      Hands-on certification covering:
      - Cluster administration and troubleshooting
      - Workload deployment and management
      - Security and networking configuration

  - degree: "Google Cloud Professional Developer"
    university: "Google Cloud Platform"
    time: "2021"
    details: |
      Advanced certification in cloud-native development:
      - Microservices architecture patterns
      - CI/CD pipeline implementation
      - Monitoring and debugging applications
```

### Publications Component

**File**: `_includes/publications.html`

**Academic Publications Example**:
```yaml
# _data/data.yml
publications:
  title: "Publications & Research"
  intro: |
    Peer-reviewed publications and conference presentations in software
    engineering and machine learning.

  papers:
    - title: "Scalable Microservices Architecture for E-commerce Platforms"
      authors: "John Doe, Jane Smith, Bob Johnson"
      conference: "International Conference on Software Engineering (ICSE 2023)"

    - title: "Machine Learning Approaches for Code Quality Assessment"
      authors: "John Doe, Alice Brown"
      conference: "ACM Transactions on Software Engineering, Vol. 49, No. 3 (2023)"

    - title: "Performance Optimization in Single-Page Applications"
      authors: "John Doe"
      conference: "Web Performance Conference, Amsterdam (2022)"

    - title: "Automated Testing Strategies for Microservices"
      authors: "John Doe, Carol White, David Lee"
      conference: "IEEE Software, Vol. 39, No. 2 (2022)"
```

**Technical Articles Example**:
```yaml
publications:
  title: "Technical Writing"
  intro: |
    Technical articles and blog posts sharing knowledge and insights
    from real-world development experience.

  papers:
    - title: "Building Resilient APIs with Node.js and Express"
      authors: "John Doe"
      conference: "Published on Medium - 50K+ views (2023)"

    - title: "React Performance: A Comprehensive Guide"
      authors: "John Doe"
      conference: "Dev.to Featured Article - 25K+ reads (2023)"

    - title: "Docker Best Practices for Development Teams"
      authors: "John Doe"
      conference: "Company Tech Blog - Internal Publication (2022)"

    - title: "Introduction to GraphQL for REST Developers"
      authors: "John Doe"
      conference: "FreeCodeCamp Publication - 15K+ claps (2022)"
```

## Advanced Customization

### Custom Section Creation

**Step 1**: Create the include file
```html
<!-- _includes/certifications.html -->
{% assign certs = site.data.data.certifications %}
{% if certs %}
<section class="section certifications-section">
  <h2 class="section-title">
    <span class="fa-stack fa-xs">
      <i class="fas fa-circle fa-stack-2x"></i>
      <i class="fas fa-certificate fa-stack-1x fa-inverse"></i>
    </span>
    {{ certs.title }}
  </h2>

  {% if certs.intro %}
  <div class="intro">{{ certs.intro }}</div>
  {% endif %}

  {% for cert in certs.items %}
  <div class="item">
    <div class="cert-header">
      <h3 class="cert-title">{{ cert.name }}</h3>
      <span class="cert-date">{{ cert.date }}</span>
    </div>
    <div class="cert-issuer">{{ cert.issuer }}</div>
    {% if cert.credential %}
    <div class="cert-credential">
      <a href="{{ cert.credential }}" target="_blank">View Credential</a>
    </div>
    {% endif %}
    {% if cert.description %}
    <div class="cert-description">{{ cert.description }}</div>
    {% endif %}
  </div>
  {% endfor %}
</section>
{% endif %}
```

**Step 2**: Add data structure
```yaml
# _data/data.yml
certifications:
  title: "Certifications"
  intro: "Professional certifications and achievements"
  items:
    - name: "AWS Certified Solutions Architect"
      issuer: "Amazon Web Services"
      date: "2023"
      credential: "https://aws.amazon.com/verification"
      description: "Professional-level certification for cloud architecture"
    
    - name: "Certified Kubernetes Administrator"
      issuer: "CNCF"
      date: "2022" 
      credential: "https://training.linuxfoundation.org/certification/verify"
      description: "Hands-on Kubernetes cluster administration"
```

**Step 3**: Include in layout
```html
<!-- index.html -->
{% include certifications.html %}
```

**Step 4**: Add custom styles
```scss
// _sass/_base.scss or custom file
.certifications-section {
  .cert-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 5px;
  }
  
  .cert-title {
    margin: 0;
    color: $theme-color;
  }
  
  .cert-date {
    font-weight: bold;
    color: $text-color-secondary;
  }
  
  .cert-issuer {
    font-style: italic;
    margin-bottom: 5px;
  }
  
  .cert-credential a {
    color: $link-color;
    text-decoration: none;
    
    &:hover {
      color: $link-hover-color;
      text-decoration: underline;
    }
  }
}
```

### Multi-language Resume Support

**Create language-specific data files:**
```yaml
# _data/data.yml (English - default)
sidebar:
  name: "John Doe"
  tagline: "Software Engineer"
  # ... rest of English content

# _data/data_es.yml (Spanish)
sidebar:
  name: "John Doe"
  tagline: "Ingeniero de Software"
  # ... Spanish translations
```

**Language switcher component:**
```html
<!-- _includes/language-switcher.html -->
<div class="language-switcher">
  <a href="{{ site.baseurl }}/" class="lang-link {% if page.lang == 'en' or page.lang == nil %}active{% endif %}">EN</a>
  <a href="{{ site.baseurl }}/es/" class="lang-link {% if page.lang == 'es' %}active{% endif %}">ES</a>
</div>
```

**Language-specific pages:**
```html
<!-- index.html (English) -->
---
layout: default
lang: en
---
{% assign data = site.data.data %}
<!-- Use English data -->

<!-- es/index.html (Spanish) -->
---
layout: default
lang: es
---
{% assign data = site.data.data_es %}
<!-- Use Spanish data -->
```

### Theme Customization Examples

**Dark Mode Theme:**
```scss
// _sass/skins/_dark.scss
$theme-color: #00d4aa;
$text-color: #e4e6ea;
$text-color-secondary: #b0b3b8;
$text-muted: #8a8d91;
$divider: #3e4042;
$lighter-gray: #242526;
$darker-gray: #18191a;
$sidebar-bg: #242526;
$link-color: #00d4aa;
$link-hover-color: #00b894;

// Dark mode specific styles
body {
  background-color: $darker-gray;
  color: $text-color;
}

.wrapper {
  background-color: $darker-gray;
}

.main-wrapper {
  background-color: $lighter-gray;
}
```

**Corporate Theme:**
```scss
// _sass/skins/_corporate.scss
$theme-color: #2c3e50;
$text-color: #2c3e50;
$text-color-secondary: #7f8c8d;
$text-muted: #95a5a6;
$divider: #ecf0f1;
$lighter-gray: #f8f9fa;
$darker-gray: #e9ecef;
$sidebar-bg: #34495e;
$link-color: #3498db;
$link-hover-color: #2980b9;

// Corporate styling
.section-title {
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: 600;
}

.sidebar-wrapper {
  border-right: 3px solid $theme-color;
}
```

## Performance Optimization

### Image Optimization
```yaml
# Optimize profile image
sidebar:
  avatar: "profile.webp"  # Use WebP format for better compression
  # Or provide multiple formats
  avatar_webp: "profile.webp"
  avatar_jpg: "profile.jpg"
```

### Lazy Loading Implementation
```html
<!-- _includes/head.html - Add lazy loading styles -->
<style>
.lazy-load {
  opacity: 0;
  transition: opacity 0.3s;
}
.lazy-load.loaded {
  opacity: 1;
}
</style>

<!-- _includes/sidebar.html - Update avatar -->
{% if sidebar.avatar %}
<img class="avatar lazy-load" 
     data-src="{{ site.baseurl }}/assets/images/{{ sidebar.avatar }}" 
     alt="profile picture" />
{% endif %}

<!-- _includes/scripts.html - Add lazy loading JS -->
<script>
document.addEventListener('DOMContentLoaded', function() {
  const images = document.querySelectorAll('.lazy-load');
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
});
</script>
```

## SEO Optimization

### Enhanced Meta Tags
```html
<!-- _includes/head.html - Enhanced SEO -->
<meta name="author" content="{{ site.data.data.sidebar.name }}">
<meta name="description" content="{{ site.description | default: site.data.data.career-profile.summary | strip_html | truncate: 160 }}">
<meta name="keywords" content="{% for skill in site.data.data.skills.toolset %}{{ skill.name }}{% unless forloop.last %}, {% endunless %}{% endfor %}">

<!-- Open Graph -->
<meta property="og:title" content="{{ site.title }}">
<meta property="og:description" content="{{ site.description }}">
<meta property="og:image" content="{{ site.url }}{{ site.baseurl }}/assets/images/{{ site.data.data.sidebar.avatar }}">
<meta property="og:url" content="{{ site.url }}{{ site.baseurl }}">
<meta property="og:type" content="website">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="{{ site.title }}">
<meta name="twitter:description" content="{{ site.description }}">
<meta name="twitter:image" content="{{ site.url }}{{ site.baseurl }}/assets/images/{{ site.data.data.sidebar.avatar }}">

<!-- Structured Data -->
<script type="application/ld+json">
{
  "@context": "https://schema.org/",
  "@type": "Person",
  "name": "{{ site.data.data.sidebar.name }}",
  "jobTitle": "{{ site.data.data.sidebar.tagline }}",
  "email": "{{ site.data.data.sidebar.email }}",
  "url": "{{ site.url }}{{ site.baseurl }}",
  "sameAs": [
    {% if site.data.data.sidebar.linkedin %}"https://linkedin.com/in/{{ site.data.data.sidebar.linkedin }}",{% endif %}
    {% if site.data.data.sidebar.github %}"https://github.com/{{ site.data.data.sidebar.github }}",{% endif %}
    {% if site.data.data.sidebar.twitter %}"https://twitter.com/{{ site.data.data.sidebar.twitter | remove: '@' }}"{% endif %}
  ]
}
</script>
```

This comprehensive component guide provides practical examples and implementation patterns for all aspects of the Online CV theme. Use these examples as starting points for your own customizations and enhancements.