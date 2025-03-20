# Guia de Instalação para Ambiente de Desenvolvimento no Fedora

Este guia fornece instruções detalhadas para instalar e configurar Docker, Docker Compose, PECL e as extensões necessárias para PHP no Fedora.

## 1. Instalação do Docker

### Instalar o pacote `dnf-plugins-core`
```bash
sudo dnf install dnf-plugins-core
```

### Adicionar o repositório Docker

**Fedora 40:**
```bash
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
```

**Fedora 41 e mais recente:**
```bash
sudo dnf config-manager addrepo --from-repofile="https://download.docker.com/linux/fedora/docker-ce.repo"
```

### Instalar o Docker Engine
```bash
sudo dnf install docker-ce docker-ce-cli containerd.io
```

### Iniciar o serviço Docker
```bash
sudo systemctl start docker
```

### Verificar a instalação do Docker
```bash
sudo docker run hello-world
```

### Habilitar o Docker para iniciar na inicialização do sistema
```bash
sudo systemctl enable docker
```

### Permitir uso do Docker sem sudo
```bash
sudo groupadd docker && sudo gpasswd -a ${USER} docker && sudo systemctl restart docker
newgrp docker
```

> **Nota:** É necessário sair e entrar novamente ou usar o comando `newgrp docker` para aplicar as mudanças.

---

## 2. Instalação do Docker Compose
```bash
sudo yum update
sudo yum install docker-compose-plugin
```

---

## 3. Instalação do PECL
```bash
sudo dnf install pecl
```

---

## 4. Instalação de Dependências para PHP

### Instalar dependências
```bash
sudo dnf install php-devel
sudo dnf install librdkafka-devel
```

### Instalar extensão `rdkafka`
```bash
sudo pecl install rdkafka
```

### Adicionar `rdkafka` ao arquivo `/etc/php.ini`
```bash
extension=rdkafka
```

---

## 5. Instalação do MongoDB
```bash
sudo dnf install php-pecl-mongodb
```

### Verificar se a extensão está ativa
```bash
php -m | grep mongodb
```

Caso não esteja ativo, adicionar manualmente no `/etc/php.ini`:
```bash
extension=mongodb
```

---

## 6. Instalação da Extensão OpenTelemetry
```bash
pecl install opentelemetry
```

### Adicionar `opentelemetry` ao arquivo `/etc/php.ini`
```bash
extension=opentelemetry.so
```

---

## 7. Instalação da Extensão gRPC
```bash
sudo pecl install grpc
```

### Adicionar `grpc` ao arquivo `/etc/php.ini`
```bash
extension=grpc
```

---

## 8. Instalação da Extensão PHP-PDO
```bash
sudo dnf install php-pdo
```

---

## 9. Instalação de Dependências PHP via Composer
Ao rodar o comando abaixo, se alguma extensão não estiver instalada, o sistema pedirá permissão para prosseguir com a instalação:
```bash
composer install
```

---

Seguindo estas instruções na ordem apresentada, seu ambiente de desenvolvimento estará devidamente configurado. Em caso de dúvidas ou problemas, consulte as documentações oficiais.

