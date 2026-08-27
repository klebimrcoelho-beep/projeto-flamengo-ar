# WebAR — Realidade Aumentada com MindAR + A-Frame

## Estrutura do Projeto

```
app realidade aumentada/
├── index.html          ← Aplicação WebAR principal
└── assets/
    ├── video.mp4       ← ⚠️ Substitua pelo seu vídeo real
    └── alvo.mind       ← ⚠️ Gerado pelo compilador MindAR (veja abaixo)
```

---

## Como gerar o arquivo `alvo.mind`

O arquivo `alvo.mind` é gerado a partir da **imagem alvo** (a foto/embalagem do produto físico).

### Passo a passo:

1. Acesse o compilador oficial online:
   👉 **https://hiukim.github.io/mind-ar-js-doc/tools/compile**

2. Faça o upload da imagem do seu produto (JPG ou PNG, alta resolução)

3. Aguarde a compilação e baixe o arquivo `.mind` gerado

4. Coloque o arquivo em `assets/alvo.mind`

### Dicas para uma boa imagem alvo:
- Use imagens com **alto contraste** e **detalhes ricos** (evite superfícies lisas e uniformes)
- Prefira formatos **não simétricos** para melhor rastreamento
- Resolução mínima recomendada: **500 × 500 px**

---

## Como substituir o vídeo

Coloque seu arquivo de vídeo em `assets/video.mp4`.

> **Proporção do vídeo:** O `<a-video>` está configurado com `width="1" height="0.5625"` (proporção 16:9).
> Se seu vídeo for em outra proporção (ex: 1:1 ou 4:3), ajuste o atributo `height` no `index.html` conforme necessário.

---

## Como testar localmente

Como a WebAR exige câmera, você precisa servir os arquivos via **HTTPS** ou **localhost**:

```bash
# Opção 1 — Python (simples)
python -m http.server 8080

# Opção 2 — Node.js (npx)
npx serve .

# Opção 3 — Live Server (VS Code)
# Instale a extensão "Live Server" e clique em "Go Live"
```

Depois acesse no celular via `http://<seu-ip-local>:8080` ou use um túnel HTTPS (ex: **ngrok**).

---

## Bibliotecas utilizadas (CDN)

| Biblioteca | Versão | Finalidade |
|---|---|---|
| A-Frame | `1.5.0` | Motor de cena 3D/AR |
| MindAR Image Tracking | `1.2.5` | Rastreamento de imagem |

---

## Fluxo da experiência

```
Câmera ativa
    │
    ▼
Alvo detectado ──► botão "Tocar Vídeo" aparece
    │
    ▼ (usuário clica)
Vídeo toca sobre o alvo ──► botão some
    │
    ▼ (alvo sai do quadro)
Vídeo pausa + botão some + dica de busca reaparece
```
