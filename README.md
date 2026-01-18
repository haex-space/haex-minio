# haex-minio

MinIO S3-compatible object storage for haex-space.

## Overview

This provides multi-tenant S3 storage with:
- Per-user buckets (`user-{userId}`)
- Storage quotas (10GB default)
- S3-compatible API

## Deployment

Deployed via Ansible role `haex-minio` in the haex-space infrastructure.

```bash
ansible-playbook haex.space.play.yml --tags haex-minio
```

## URLs

- S3 API: `https://s3.haex.space`
- Console: `https://console.s3.haex.space`

## Integration

The `haex-sync-server` acts as a proxy between users and MinIO:
1. Users authenticate with haex-sync-server
2. Sync-server creates user buckets on-demand
3. Sync-server proxies S3 requests to MinIO with admin credentials
