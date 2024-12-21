# Single Page Navigation Implementation Guide

## Overview
This documentation explains how to implement a single-page navigation system where different sections (pages) are shown/hidden using JavaScript, without reloading the page.

## Core Components

### 1. HTML Structure
Each section of your website needs to be wrapped in a div with two key attributes:
```html
<div id="unique-section-id" class="section">
    <!-- Section content goes here -->
</div>
```

Key points:
- Each section must have a unique ID (e.g., `homepage-section`, `login-section`)
- Each section must have the `section` class
- Only one section should have the `active` class initially

Example structure:
```html
<div id="homepage-section" class="section active">   
    <!-- Homepage content -->
</div>

<div id="login-section" class="section">
    <!-- Login content -->
</div>

<div id="register-section" class="section">
    <!-- Register content -->
</div>
```

### 2. CSS Implementation
The CSS uses display properties to show/hide sections:
```css
/* Hide all sections by default */
.section { 
    display: none; 
}

/* Show only the active section */
.section.active { 
    display: block; 
}
```

How it works:
- `.section { display: none; }` hides all sections initially
- `.section.active { display: block; }` shows only the section with both classes
- This ensures only one section is visible at a time

### 3. JavaScript Navigation
The navigation is handled by a function that toggles the `active` class:
```javascript
function showSection(sectionId) {
    // Remove 'active' class from all sections
    document.querySelectorAll('.section').forEach(section => {
        section.classList.remove('active');
    });
    // Add 'active' class to the selected section
    document.getElementById(sectionId).classList.add('active');
}
```

How it works:
1. First, it removes the `active` class from all sections
2. Then, it adds the `active` class to the selected section
3. CSS rules then show the active section and hide others

### 4. Navigation Links
Links in your navigation should use the `onclick` event to trigger section changes:
```html
<a href="#" onclick="showSection('homepage-section')">Home</a>
<a href="#" onclick="showSection('login-section')">Login</a>
<a href="#" onclick="showSection('register-section')">Register</a>
```

## Common Issues and Solutions

1. **Section Not Showing**
   - Verify the section ID matches exactly in both HTML and JavaScript
   - Check that the section has both the `section` class and correct ID
   - Ensure JavaScript is loaded after HTML content

2. **Multiple Sections Showing**
   - Check that only one section has the `active` class initially
   - Verify the CSS specificity isn't being overridden
   - Make sure all sections have the `section` class

3. **Navigation Not Working**
   - Confirm JavaScript function name matches in onclick events
   - Check browser console for JavaScript errors
   - Verify section IDs are unique and correctly spelled

## Implementation Steps

1. Add the CSS to your stylesheet:
```css
.section { 
    display: none; 
}
.section.active { 
    display: block; 
}
```

2. Wrap each page section in a div with appropriate classes:
```html
<div id="section-name" class="section">
    <!-- Content -->
</div>
```

3. Add the JavaScript function to your script:
```javascript
function showSection(sectionId) {
    document.querySelectorAll('.section').forEach(section => {
        section.classList.remove('active');
    });
    document.getElementById(sectionId).classList.add('active');
}
```

4. Update navigation links with onclick handlers:
```html
<a href="#" onclick="showSection('section-name')">Link Text</a>
```

## Testing
1. Click each navigation link to verify sections change correctly
2. Check that only one section is visible at a time
3. Verify that the URL doesn't refresh when changing sections
4. Test that the initial active section displays correctly on page load

## Best Practices
- Keep section IDs descriptive and consistent
- Always include the `section` class on section containers
- Ensure JavaScript loads after HTML content
- Use meaningful names for section IDs
- Consider adding loading states for larger sections
