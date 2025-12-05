# 🚀 Terraform + Proxmox: Автоматическое создание 3 виртуальных машин

Этот проект автоматически создаёт 3 виртуальные машины на Proxmox через Terraform:

| VM Name      | VMID | Storage    | Disk | CPU   | RAM    |
|--------------|------|-----------|------|-------|--------|
| master-node  | 100  | local-lvm | 45G  | 2×2   | 6144MB |
| devops CICD  | 101  | local-lvm | 45G  | 1×4   | 4096MB |
| production   | 102  | hdd-lvm   | 50G  | 1×3   | 4096MB |

ISO: `ubuntu-22.04.5-live-server-amd64.iso`  
Network bridge: `vmbr0`  
Proxmox node: `pve`

---

## 📦 Установка Terraform на Proxmox

```bash
apt update && apt install -y gnupg software-properties-common curl

curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor -o /usr/share/keyrings/hashicorp.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" \
  > /etc/apt/sources.list.d/hashicorp.list

apt update && apt install -y terraform

⚙️ Настройка

Создай файл:

mkdir proxmox-3vm && cd proxmox-3vm
```

"Необязательно, можно вручную написать пароль" Перед запуском создай файл terraform.tfvars:

pm_user     = "root@pam"
pm_password = "ТВОЙ_ПАРОЛЬ"
