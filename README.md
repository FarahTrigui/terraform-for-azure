# Provisionnement Azure avec Terraform

Ce projet automatise le déploiement d'une infrastructure cloud sur Microsoft Azure en utilisant Terraform. Il permet de créer une machine virtuelle Ubuntu et les ressources réseau nécessaires, tout en générant une paire de clés SSH pour l'accès sécurisé.

## 🚀 Fonctionnalités

- Création d’un Resource Group
- Déploiement d’un réseau virtuel (VNet) et d’un sous-réseau
- Attribution d’une adresse IP publique dynamique
- Création d’une interface réseau (NIC)
- Déploiement d'une machine virtuelle Ubuntu avec une clé SSH
- Génération automatique de clés SSH locales

## 📦 Structure Terraform (extrait)

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = "rg-terraform"
  location = "East US"
}

# VNet, Subnet, IP, NIC, VM, SSH key...
```

## 🔑 Accès SSH

Une paire de clés RSA est générée automatiquement à l'aide du provider `tls`. La clé publique est injectée dans la VM, et la clé privée est sauvegardée localement.

## 🛠️ Prérequis

- Terraform installé (v1.0+ recommandé)
- Un compte Azure avec accès au portail
- Azure CLI authentifié (`az login`)
- Permissions suffisantes pour créer des ressources

## 📌 Déploiement

```bash
terraform init
terraform apply
```

À la fin, l’adresse IP publique de la VM sera affichée pour un accès SSH :

```bash
ssh -i id_rsa azureuser@<IP>
```

## 🧹 Nettoyage

```bash
terraform destroy
```

## 📁 Fichiers générés

- `id_rsa`: Clé privée SSH
- `id_rsa.pub`: Clé publique SSH injectée dans la VM

## 🧑‍💻 Auteur

Farah Trigui – [LinkedIn](https://www.linkedin.com/in/farah-trigui-a4474821a/) | [GitHub](https://github.com/FarahTrigui)
