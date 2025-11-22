# 🌐 Global Solution 2025 – Portal IA

## 📚 Sobre o Projeto
Este projeto faz parte da disciplina de **Network Architect Solutions** e tem como objetivo demonstrar uma **arquitetura simples de rede** para suporte a Inteligência Artificial e a publicação de um portal web estático representando o fluxo:

Data Lab → AI Services → Users (Frontend)

O trabalho é dividido em duas partes principais: **rede IPv4 no Packet Tracer** e **deploy de um site usando Docker + Nginx**.

## 🖧 Parte 1 – Rede IPv4 (Packet Tracer)

### 🟢 Estrutura
- **1 roteador**
- **1 switch**
- **6 hosts** distribuídos:
  - 2 → Data Lab
  - 2 → AI Services
  - 2 → Users/Frontend
- Sub-redes derivadas de `192.168.100.0/24` com máscara `/29` (`255.255.255.248`)

### 🔹 Tabela de Sub-redes

| Sub-rede       | IP Inicial     | IP Final       | Gateway        |
|----------------|---------------|----------------|----------------|
| Data Lab       | 192.168.100.2 | 192.168.100.6  | 192.168.100.1  |
| AI Services    | 192.168.100.10| 192.168.100.14 | 192.168.100.9  |
| Users/Frontend | 192.168.100.18| 192.168.100.22 | 192.168.100.17 |

### 🔹 Topologia
- Todos os hosts conectados ao switch
- Switch conectado ao roteador
- Configuração de IPs estáticos nos hosts
- Default Gateway de cada host configurado como IP do roteador da sub-rede correspondente

### 🔹 Testes realizados
- Ping de cada host para o gateway da sua sub-rede ✅
- Ping entre hosts da mesma sub-rede ✅

📁 Arquivo Packet Tracer: `gs_redes_2sem.pkt`

---

## 🖥️ Parte 2 – Portal IA com Docker/Nginx

### 🔹 Estrutura do Site
- Pasta: `site/`
- Arquivos principais:
  - `index.html` → conteúdo do portal explicando o fluxo
  - `style.css` → estilização do portal

### 🔹 Tecnologias
- HTML5
- CSS3 
- Docker + Nginx para servir arquivos estáticos

### 🔹 Comando Docker

```bash
docker run -d \
  --name portal-ia \
  -p 8080:80 \
  -v ${PWD}/site/:/usr/share/nginx/html:ro \
  nginx:latest
```


