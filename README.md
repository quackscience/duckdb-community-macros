[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![GitHub stars](https://img.shields.io/github/stars/nelsontky/gh-pages-url-shortener?style=social)

# GitHub Pages URL Shortener

A simple yet powerful URL shortener that uses GitHub Pages, GitHub Issues, and repository files for URL redirection. No extra hosting or database needed!

## How It Works

This URL shortener supports two methods of creating short URLs:

1. **Issue-based links** (`/i/` routes)
   - Uses GitHub Issues to store URLs
   - Great for automation and quick additions
   - URLs are stored in issue titles

2. **File-based links** (`/r/` routes)
   - Uses files in the `/links` directory
   - Perfect for memorable, custom-named shortcuts
   - URLs are stored in file contents

## Setting Up Your Own Instance

1. Fork this repository
2. Enable GitHub Pages in your repository settings:
   - Go to Settings → Pages
   - Set Source to "GitHub Actions"
   - Your site will be available at `https://[username].github.io/[repo-name]/`

3. Update the configuration in `index.html`:
   ```javascript
   const CONFIG = {
     GITHUB_ISSUES_LINK: "https://api.github.com/repos/YOUR_USERNAME/YOUR_REPO/issues/",
     GITHUB_FILES_LINK: "https://api.github.com/repos/YOUR_USERNAME/YOUR_REPO/contents/links/",
     GITHUB_REPO: "https://github.com/YOUR_USERNAME/YOUR_REPO"
   };
   ```

## Creating Short URLs

### Method 1: Issue-Based Links (`/i/`)

1. Create a new issue in your repository
2. Set the issue title to your destination URL
   - Example: `https://www.google.com`
3. Note the issue number (e.g., `123`)
4. Your short URL will be: `https://[username].github.io/[repo-name]/i/123`

**Pros of Issue-Based Links:**
- Quick to create via GitHub UI or API
- Easy to automate with GitHub Actions
- Built-in history and modification tracking
- Can add notes in issue comments

### Method 2: File-Based Links (`/r/`)

1. Navigate to the `/links` directory in your repository
2. Create a new file with your desired short name
   - Example: Create file `google`
3. Add your destination URL as the only content
   - Example: `https://www.google.com`
4. Your short URL will be: `https://[username].github.io/[repo-name]/r/google`

**Pros of File-Based Links:**
- Custom, memorable URLs
- Easy to manage with git
- Can be organized in bulk
- Great for permanent links

## Examples

```
# Issue-based links
/i/123 → Issue #123's title URL
/i/456 → Issue #456's title URL

# File-based links
/r/google → Contents of /links/google file
/r/github → Contents of /links/github file

# Invalid routes redirect to repository
/anything-else → GitHub repository
```

## Tips and Best Practices

### For Issue-Based Links:
1. Use clear issue labels to organize your URLs
2. Add descriptions in issue comments for context
3. Close issues for deprecated URLs
4. Use issue numbers sequentially for easy tracking

### For File-Based Links:
1. Use lowercase filenames for consistency
2. Avoid special characters in filenames
3. Organize related links with similar names
4. Keep one URL per file

## Technical Details

- The shortener uses client-side JavaScript to handle redirects
- GitHub's API is used to fetch both issues and files
- All redirects are handled through GitHub Pages
- No server-side code or database required

## Limitations

#### GitHub Pages Update Time:
   - File-based links may take a few minutes to update
   - Issue-based links are immediate

#### URL Requirements:
   - Must be valid URLs starting with http:// or https://
   - Cannot redirect to the shortener domain itself

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
