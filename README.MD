# Instalação do Git e Insomnia no Fedora

## Instalação do Git

Para instalar o Git no Fedora, execute o seguinte comando:

```bash
sudo dnf install git
```

### Verificar a instalação
Para verificar se o Git foi instalado corretamente:

```bash
git --version
```

Para mais informações, visite a [documentação oficial do Git](https://git-scm.com/downloads/linux).

---

## Instalação do Insomnia

### 1. Instalar o Snap
O Insomnia é distribuído via Snap. Para instalar o Snap no Fedora, utilize o comando:

```bash
sudo dnf install snapd
```

### 2. Instalar o Insomnia
Após instalar o Snap, utilize o seguinte comando para instalar o Insomnia:

```bash
sudo snap install insomnia
```

### 3. Executar o Insomnia
Para rodar o Insomnia, utilize:

```bash
snap run insomnia
```

Para mais detalhes, consulte a [documentação oficial do Insomnia](https://docs.insomnia.rest/insomnia/install).

