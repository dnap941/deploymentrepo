# Software Deployment Repository

Software distribution repository for delivering installers and deployment packages to users and managed endpoints when an RMM platform cannot host the files itself, commonly because packages exceed its approximately 500 MB upload limit.

## Distribution

Publish installer packages as GitHub Release assets rather than committing large binaries to Git history. RMM jobs and users can download the assets through their HTTPS release URLs. Each release asset must be under GitHub's 2 GiB limit.

This repository is intentionally public so users and RMM jobs can download packages without GitHub authentication. Anyone can view and download published assets. Changing the repository to private requires authenticated downloads or a separately configured distribution service; existing anonymous download workflows must be migrated first.

## Publishing baseline

- Distribute only software that is authorized for public redistribution.
- Never upload passwords, unattended-access credentials, private keys, license keys, customer data, or tenant-specific enrollment tokens, including inside ZIP archives or bundled configuration.
- Check packages against trusted vendor sources and verify signatures where available.
- Use version-specific release assets and record their SHA-256 hashes in deployment jobs before executing downloaded content. Keep the expected hash in a separately controlled script or configuration.
- Restrict write access to trusted maintainers and secure publishing accounts with multifactor authentication.
- Review package contents before publishing and remove obsolete packages after confirming no deployment jobs still depend on them.

Public availability does not permit unauthenticated modification. Package integrity and the security of publishing access are essential because endpoints may execute downloaded installers with elevated privileges.
