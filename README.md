# ⚙️ workstation-bootstrap-ansible

Trimmed down version aimed to be used with `ansible-pull` after a clean install

---

## 🚀 Key Features

* **Idempotent Setup:** Uses Ansible to ensure the system configuration is consistent and repeatable.
* **Dotfile Management:** Initializes and applies dotfiles using **Chezmoi** immediately after all dependencies are installed.

---

## 📋 Prerequisites

To run this playbook, you need a working Ansible control node to the target host.

1.  **Target Host (`ansible_tester_fedora`):**
    * A clean install of **Fedora** or **RHEL based distribution**.
    * The target user

---

## 🛠️ Usage

Run with `ansible-pull`
