# Design Decisions

## S3 vs EC2

S3 was selected because:

- No server management required
- Highly scalable and durable
- Lower cost for static content

---

## Private Origin Design

The S3 bucket is not publicly accessible.

Benefits:

- Prevents direct access to origin
- Ensures all traffic flows through CloudFront
- Improves overall security posture

---

## CloudFront for CDN

CloudFront is used as the CDN layer in front of S3.

Reasons:

- Native integration with AWS services
- Efficient caching and global distribution
- Supports secure origin access patterns

---

## Cloudflare for DNS and TLS

Cloudflare was selected for DNS and TLS management.

Reasons:

- Free DNS hosting
- Simplified TLS configuration
- Email routing support for custom domain

This allows use of a custom email address (nicholas@frost.vip) without additional cost.

---

## Hybrid Architecture Approach

This project uses both Cloudflare and CloudFront.

Benefits:

- Combines Cloudflare DNS and domain features with AWS CDN capabilities
- Demonstrates understanding of multi-provider architectures
- Reflects real-world design flexibility