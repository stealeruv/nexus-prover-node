# nexus-prover-node
$27.2M Nexus Prover Node Cli setup using a service file to run 24/7

Unlock the Power of Verifiable Computation

Site : [Nexus](https://nexus.xyz/) | X : [NexusLabs](https://x.com/NexusLabsHQ) | Docs : [Nexus docs](https://docs.nexus.xyz/)



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

Credit Card/Paypal/Crypto Credit card : 

💻 **Contabo VPS Options! 🚀**  

📌 **VPS 1**  
🔗 [Contabo VPS 1](https://www.jdoqocy.com/click-101278318-15692486)
**4 vCPU Cores | 4 GB RAM | 100 GB NVMe or 400 GB SSD | 1 Snapshot | 32 TB Traffic* | Unlimited Incoming**  

📌 **VPS 2**  
🔗 [Contabo VPS 2](https://www.anrdoezrs.net/click-101278318-13796472) 
**6 vCPU Cores | 16 GB RAM | 200 GB NVMe or 400 GB SSD | 2 Snapshots | 32 TB Traffic* | Unlimited Incoming**  

📌 **VPS 3**  
🔗 [Contabo VPS 3](https://www.dpbolvw.net/click-101278318-13796474)
**8 vCPU Cores | 24 GB RAM | 300 GB NVMe or 1.2 TB SSD | 2 Snapshots | 32 TB Traffic* | Unlimited Incoming**  

📌 **VPS 4**  
🔗 [Contabo VPS 4](https://www.anrdoezrs.net/click-101278318-13796476)
**12 vCPU Cores | 48 GB RAM | 400 GB NVMe or 1.6 TB SSD | 3 Snapshots | 32 TB Traffic* | Unlimited Incoming**  

💡 **Get started with the perfect VPS for your needs!** 🚀

---

### Step 1: Install Dependencies
```bash
sudo apt update && sudo apt upgrade
sudo apt install build-essential pkg-config libssl-dev git-all
```

---

### Step 2: Install Rust(Existing users Skip this process)
```bash
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
export PATH="$HOME/.cargo/bin:$PATH"
source ~/.bashrc
rustc --version
```

**Remove existing folder and services**

```
sudo systemctl stop nexus.service
sudo systemctl disable nexus.service
rm -rf nexus-cli
```

---

### Step 3: Clone Nexus Repository
```bash
git clone https://github.com/nexus-xyz/network-api.git "$HOME/nexus-cli"
cd nexus-cli/clients/cli
```

### Install protoc
```
sudo apt update
sudo apt install -y protobuf-compiler
protoc --version
```

result should be **libprotoc 3.21.5**

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
sudo systemctl enable nexus.service
sudo systemctl start nexus.service
```

---

---

### Step 6: View Nexus Service Logs
```bash
journalctl -u nexus.service -fn 50
```

---

### Step 7: Get Prover ID
```bash
cat $HOME/.nexus/prover-id
```

## ProverID Update

Goto : https://beta.nexus.xyz/

Connect and Verify Email, then copy the prover ID (left corner)

Login to VPS 

Run
```
nano $HOME/.nexus/prover-id
```

Replace the browser proverID then Press CTRL + X, and Press Y and Press Enter.

```
sudo systemctl restart nexus.service
```

Check Logs

```bash
journalctl -u nexus.service -fn 50
```

Follow : x.com/cryptoconsol
