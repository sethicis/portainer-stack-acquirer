# portioner-stack-template

Template repository for Portainer GitOps stacks deployed from GitHub.

## What this template includes

- `docker-compose.yml` - Stack definition that Portainer deploys.
- `stack.env` - Environment variables loaded by the stack.
- `.github/dependabot.yml` - Dependency update automation for Docker images.
- `.github/workflows/portainer-gitops-update.yml` - Triggers your Portainer GitOps webhook on pushes to `main`.
- `.github/workflows/docker-style-check.yml` - Lints Dockerfiles and `docker-compose` files on pull requests.

## How to use

1. Click **Use this template** and create a new repository.
2. Replace `docker-compose.yml` with your stack services.
3. Update `stack.env` with environment values required by your compose file.
4. In GitHub repository settings, set `PORTAINER_HOOK` as an Actions variable (recommended in an Environment) containing your Portainer stack webhook URL.
5. Merge changes to `main` to trigger an automatic Portainer refresh.

## Configure after creating a new stack repository

- Service names, images, ports, volumes, and networks in `docker-compose.yml`.
- Environment variables in `stack.env`.
- Optional Dependabot schedule/labels in `.github/dependabot.yml`.
- Optional linter rules and scope in `.github/workflows/docker-style-check.yml`.
