# ⚙️ workstation-bootstrap-ansible

A collection of Ansible playbooks designed to set up a personal RHEL based Linux workstation environment from a minimal install. This process installs core development tools (Rust, Go), system packages, and bootstraps user-level configurations using **Chezmoi** and my public dotfiles repository.

---

## 🚀 Key Features

* **Idempotent Setup:** Uses Ansible to ensure the system configuration is consistent and repeatable.
* **Package Management:** Installs core packages like `neovim`, `fish`, `wezterm`, `chezmoi`, `rust`, and `go`.
* **Rust Toolchain:** Uses the `community.general.cargo` module to install crucial Rust tools (`zellij`, `eza`, `zoxide`, etc.).
* **Dotfile Management:** Initializes and applies dotfiles using **Chezmoi** immediately after all dependencies are installed.

---

## 📋 Prerequisites

To run this playbook, you need a working Ansible control node and SSH access to the target host.

1.  **Ansible Control Node:**
    * Ansible installed (version 2.9+ recommended).
2.  **Target Host (`ansible_tester_fedora`):**
    * A clean install of **Fedora** or **RHEL based distribution**.
    * The target user (`CP` in the examples) must have **sudo privileges** and be accessible via **SSH key**.

---

## 🛠️ Usage

### 1. Configure Local Inventory

Since the sensitive inventory file (`inventory.ini`) is **not committed** to this repository, you must create it locally.

Create an `inventory.ini` in the root of your project directory:

```ini
[all:vars]
# Ensure the SSH user has correct permissions and keys
ansible_user=USER
# NOTE: Pass your private key path via the CLI or your local SSH agent,
# DO NOT include a sensitive path in files intended for Git.
# ansible_private_key_file=~/.ssh/id_ed25519

[workstations]
# Replace 'your.target.ip' with the actual IP or hostname
ansible_tester_fedora ansible_host=your.target.ip
```

### 2. Run the Playbook

Execute the playbook with the following command, passing your inventory file and any extra variables:

`ansible-playbook -i inventory.ini setup_workstation.yml`

#### Extra Variables

You can customize the playbook execution using `--extra-vars`:

*   `install_gui_packages`: (boolean, default: `false`) - Set to `true` to install GUI applications and their corresponding package repositories.
