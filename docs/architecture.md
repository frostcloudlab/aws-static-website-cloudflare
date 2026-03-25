# Architecture

## High-Level Design

Client  
→ Cloudflare (DNS, TLS)  
→ CloudFront (CDN, caching)  
→ Amazon S3 (private origin)

---

## Components

### Cloudflare

- DNS provider for frost.vip
- TLS termination (HTTPS)
- Handles incoming requests at the domain level

---

### Amazon CloudFront

- Global CDN for caching and performance
- Distributes content closer to users
- Fetches content from S3 origin when not cached

---

### Amazon S3

- Hosts static website content
- Configured as a private bucket
- Serves as the origin for CloudFront

---

## Request Flow

1. User requests https://frost.vip
2. DNS resolves via Cloudflare
3. Request is processed with TLS at Cloudflare
4. Request is forwarded to CloudFront
5. CloudFront serves cached content if available
6. If not cached, CloudFront retrieves content from S3
7. Response is returned to the user

---

## Benefits

- Low latency via global CDN (CloudFront)
- Secure origin with no public S3 access
- Separation of DNS and CDN responsibilities
- Scalable and cost-efficient architecture