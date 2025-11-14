```
#!/bin/bash
set -e  # Exit on any error

echo "Configuring sandbox environment..."

# 1. Clone your repository using GitHub token
echo "Cloning repository..."
git clone <https://x-access-token:${GITHUB_TOKEN}@github.com/username/repo.git> $$HOME/workspace
cd $$HOME/workspace
echo "✓ Repository cloned"

# 2. Make environment variables persistent for all future commands
echo "Setting up environment variables..."
cat >> ~/.bashrc <<'EOF'

# Add selected env variables to sandbox from local
export GITHUB_TOKEN="${GITHUB_TOKEN}"
export FAL_API_KEY="${FAL_API_KEY}"

# Auto-navigate to workspace
cd $$HOME/workspace
EOF

# 3. Activate the environment
source ~/.bashrc
echo "✓ Environment configured"
```
