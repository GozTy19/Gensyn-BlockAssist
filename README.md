# Gensyn-BlockAssist
How to run BlockAssist (Gensyn)

**BlockAssist is an AI bot that learns from you in Minecraft. It starts dumb but gets smarter as you play.**

## ➡️ Hardware Requirements
* 8 GB RAM minimum (16 GB recommended)
* Multi‑core CPU
* 10 GB disk space

---

## ➡️ Enviorement
### Local systems (Best)
### Sunshine/Moonlight (Good)
### VNC (Okay)
### RDP (Bad)

---

## ➡️ Installation
### Step 1: Install Dependecies
```bash
sudo apt update
sudo apt install -y \
  make build-essential gcc \
  libssl-dev zlib1g-dev libbz2-dev libreadline-dev \
  libsqlite3-dev libncursesw5-dev xz-utils tk-dev \
  libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev \
  curl git unzip \
  libxi6 libxrender1 libxtst6 libxrandr2 libglu1-mesa libopenal1
```

### Step 2: Clone the repo and enter the directory
```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

### Step 3: Install Node.js (Skip this if you already have Node.js > 20)
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
```

### Step 4: Install Yarn
```bash
curl -o- -L https://yarnpkg.com/install.sh | bash
export PATH="$HOME/.yarn/bin:$HOME/.config/yarn/global/node_modules/.bin:$PATH"
```

### Step 5: Install Java
```bash
./setup.sh
exec $SHELL
```

### Step 6: Install `pyenv`
```bash
curl https://pyenv.run | bash
```
```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
```

### Step 7: Install Python
```bash
pyenv install 3.10
```
Set global version
```bash
pyenv global 3.10
```

### Step 8: Install project dependecies
```bash
pip install --upgrade pip

pip install -e . --no-cache-dir
pip install "mbag-gensyn[malmo]" --no-cache-dir

pip install psutil readchar
```

---

## ➡️ Run BlockAssist

### Start Mincraft
```bash
cd blockassist

export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"

python run.py
```
---

### Hugging Face Token
It prompts you to enter a [Hugging Face](https://huggingface.co/) API token. Create an Access Token with `Write` permissions [here](https://huggingface.co/settings/tokens) and save it

### Gensyn Testnet login
You will be prompted to login via a browser
* Open **Web Browser**, visit `http://localhost:3000`, and login to your Gensyn account.
* If you have previously logged in, this step will be skipped.
*If you run on VPS
    * 1- Open a new terminal
    * 2- Install **localtunnel**:
    * ```bash
       sudo npm install -g localtunnel
      ```
    * 3- Get a password:
       ```bash
       curl https://loca.lt/mytunnelpassword
       ```
    * 4- Get URL
       ```
       lt --port 3000
       ```
    * Visit the prompted url, and enter your IP to access Gensyn login page

 ---

 ### Play Minecraft
* Wait until two Minecraft windows have opened
* Press `ENTER` in terminal.
* Go to the first Minecraft window, the game and the map should start itself, must not create one yourself.
* **Note for VNC users**: To enable in-game keys, Press `ENTER` inside the game window.
* **Note for VirtualBOX users**: To enable in-vm mouse movement, VM window > Input > Mouse Integration, then toggle off/on with `right-ctrl`
* Build the building to increase your progress. (More progress = Better trained AI).
  * Left-click pickaxe to remove, Left-click *Dirt* on red tiles, Right-click stone, glasses, plonks on place holders.
* Then return to your terminal and press `ENTER` to end the session.

**Note: Even if you don't finish the eposide till the end and close it, you'll earn your participation in the leaderboard**

### Training
A model will be started training now and be submitted to Hugging Face and to Gensyn’s smart contract.

### Verify
If you reach this stage in the logging window and can see a transaction in the block explorer, your submission has succeeded.
