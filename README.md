# HashVault Linux Package Repository

APT and DNF package repositories for HashVault mining software, hosted on GitHub Pages.

## Packages

| Package | Description |
|---------|-------------|
| vltrig | High performance RandomX CPU miner |
| vltrig-proxy | Stratum mining proxy |

## Quick install

**APT (Ubuntu / Debian):**

```
curl -fsSL https://hashvault.github.io/apt/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashvault.gpg && echo "deb [arch=amd64 signed-by=/usr/share/keyrings/hashvault.gpg] https://hashvault.github.io/apt stable main" | sudo tee /etc/apt/sources.list.d/hashvault.list && sudo apt update && sudo apt install -y vltrig
```

**DNF (Fedora / RHEL):**

```
sudo rpm --import https://hashvault.github.io/rpm/KEY.gpg && sudo tee /etc/yum.repos.d/hashvault.repo <<< $'[hashvault]\nname=HashVault\nbaseurl=https://hashvault.github.io/rpm\ngpgcheck=1\ngpgkey=https://hashvault.github.io/rpm/KEY.gpg\nenabled=1' && sudo dnf install -y vltrig
```

Replace `vltrig` with `vltrig-proxy` to install the proxy instead.

## APT (Ubuntu / Debian) - step by step

```bash
# Add the GPG key
curl -fsSL https://hashvault.github.io/apt/KEY.gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashvault.gpg

# Add the repository
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/hashvault.gpg] https://hashvault.github.io/apt stable main" | sudo tee /etc/apt/sources.list.d/hashvault.list

# Install
sudo apt update
sudo apt install vltrig          # miner
sudo apt install vltrig-proxy    # proxy
```

## DNF (Fedora / RHEL) - step by step

```bash
# Import the GPG key
sudo rpm --import https://hashvault.github.io/rpm/KEY.gpg

# Add the repository
sudo tee /etc/yum.repos.d/hashvault.repo << 'EOF'
[hashvault]
name=HashVault
baseurl=https://hashvault.github.io/rpm
gpgcheck=1
gpgkey=https://hashvault.github.io/rpm/KEY.gpg
enabled=1
EOF

# Install
sudo dnf install vltrig          # miner
sudo dnf install vltrig-proxy    # proxy
```

## Repository structure

```
apt/
  KEY.gpg
  dists/stable/main/binary-amd64/
  pool/main/
rpm/
  KEY.gpg
  repodata/
```

Repositories are updated automatically by the vltrig and vltrig-proxy release workflows.

## Links

- https://hashvault.pro - HashVault Mining Pool
- https://github.com/HashVault/vltrig
- https://github.com/HashVault/vltrig-proxy
