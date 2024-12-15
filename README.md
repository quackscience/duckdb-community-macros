# URL Shortener & Proxy Service

A simple URL shortener and proxy service using Github Pages and Cloudflare Workers. All URLs are stored as files in the `/links` directory.

## How it Works

1. Create a file in the `/links` directory
2. File name becomes your URL path
3. File content is the target URL
4. Access via `/r/your-path`

## Example

File: `/links/duckdb`

```
https://duckdb.org
```

Now `/r/duckdb` will proxy content from Google.

## Adding New URLs

1. Fork this repository
2. Create a new file in the `/links` directory
3. Name it what you want your URL path to be
4. Put the target URL as the only content
5. Submit a Pull Request

## File Requirements

- Filenames: Use only lowercase letters, numbers, and hyphens
- Content: Single line with the target URL
- URLs must be valid and publicly accessible

## How URLs are Served

Instead of redirecting, this service proxies the content directly. This means:
- Content is served from our domain
- CORS headers are properly handled
- Great for WASM and other clients that need direct access

## Contributing

PRs are welcome! Please follow the PR template when adding new URLs.

## License

MIT
