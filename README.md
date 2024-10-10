# nexus-prover-node
$25M Nexus Prover Node Cli setup using a service file to run 24/7


# Join Crypto Console Community

Join TG : [Crypto Console Telegram](https://t.me/cryptoconsol) 

Follow X : [Crypto Console Twitter](https://www.x.com/cryptoconsol) 

Subscribe : [Crypto Console Youtube](https://www.youtube.com/@cryptoconsole)

## Hardware requirements:

| **Hardware** | **Minimum Requirement** |
|--------------|-------------------------|
| **CPU**      | 6 Cores                 |
| **RAM**      | 4 GB                    | 
| **Disk**     | 50  GB  SSD             |


# VPS Options

VPS 1 is enough for Nexus Prover

Credit Card/Paypal : 

VPS 1 : [Contabo: Cloud VPS 1](https://www.jdoqocy.com/click-101278318-15692486) 

VPS 2 : [Contabo: Cloud VPS 2](https://www.tkqlhce.com/click-101278318-13796472)

VPS 3 : [Contabo: Cloud VPS 3](https://www.dpbolvw.net/click-101278318-13796474)

VPS 4 : [Contabo: Cloud VPS 3](https://www.anrdoezrs.net/click-101278318-13796476)

---

### Step 1: Install Dependencies
```bash
sudo apt update && sudo apt install -y git pkg-config libssl-dev build-essential curl
```

---

### Step 2: Install Rust
```bash
curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env

# Add Rust to the PATH permanently (if not already added)
echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# Verify Rust installation
rustc --version
```

---

### Step 3: Clone Nexus Repository (if it doesn't already exist)
```bash
if [ ! -d "$HOME/nexus-cli" ]; then
    echo "Cloning Nexus-XYZ network API repository..."
    git clone https://github.com/nexus-xyz/network-api.git "$HOME/nexus-cli"
else
    echo "Repository already exists. Skipping cloning."
fi
```

---

### Step 4: Create Systemd Service File for Nexus Prover
```bash
sudo tee /etc/systemd/system/nexus.service <<EOF
[Unit]
Description=Nexus Prover Cli
After=network.target

[Service]
User=$USER
WorkingDirectory=$HOME/nexus-cli/clients/cli
Environment=TERM=dumb
ExecStart=$HOME/.cargo/bin/cargo run --release --bin prover -- beta.orchestrator.nexus.xyz
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
EOF
```

---

### Step 5: Reload Systemd, Start, and Enable the Nexus Service
```bash
sudo systemctl daemon-reload
sudo systemctl start nexus.service
sudo systemctl enable nexus.service
```

---

### Step 6: Fixing unused imports

```bash
cargo fix --bin "prover"
```

---

### Step 7: View Nexus Service Logs
```bash
journalctl -u nexus.service -fn 50
```

---

### Step 8: Get Prover ID
```bash
cat $HOME/.nexus/prover-id
```
