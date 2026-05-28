<div align="center">

# 🤖 Autocomplete Gratuito no VSCode com Continue + Ollama

### Configure autocomplete de código com IA de forma **100% gratuita e offline** ⚡
##### Sem API key. Sem assinatura. Sem dados saindo da sua máquina.

![VSCode](https://img.shields.io/badge/VSCode-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white)
![Continue](https://img.shields.io/badge/Continue-2962FF?style=for-the-badge&logo=react&logoColor=white)
![Offline](https://img.shields.io/badge/100%25-Offline-success?style=for-the-badge)
![Free](https://img.shields.io/badge/100%25-Gratuito-blueviolet?style=for-the-badge)

</div>

---

## 🧰 O que você vai instalar

| Ferramenta | Função |
|---|---|
| 🧩 [**Continue**](https://marketplace.visualstudio.com/items?itemName=Continue.continue) | Extensão do VSCode que gerencia o autocomplete |
| 🦙 [**Ollama**](https://ollama.com) | Roda modelos de IA localmente no seu computador |
| 🧠 **qwen2.5-coder** | Modelo de IA especializado em código |

---

## 1️⃣ Instalar a extensão Continue no VSCode

1. Abra o **VSCode**
2. Vá em **Extensions** (<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>X</kbd>)
3. Pesquise por `Continue`
4. Instale a extensão **"Continue - open-source AI code agent"** (publicada por *Continue.dev*)

---

## 2️⃣ Instalar o Ollama

1. Acesse [**ollama.com**](https://ollama.com) e baixe o instalador para o seu sistema operacional
2. Instale normalmente
3. Após instalar, o Ollama ficará rodando em segundo plano em `http://localhost:11434`

> [!NOTE]
> No Windows o Ollama inicia automaticamente junto com o sistema. 🟢

---

## 3️⃣ Baixar os modelos

Abra o terminal do VSCode (<kbd>Ctrl</kbd> + <kbd>`</kbd>) e rode os comandos abaixo, **um por um**:

```bash
# 🪶 Modelo de autocomplete — leve e rápido
ollama pull qwen2.5-coder:1.5b-base
```

```bash
# 💬 Modelo de chat — cerca de 4.7 GB, pode demorar
ollama pull llama3.1:8b
```

```bash
# 🔎 Modelo de embeddings — usado para busca no código
ollama pull nomic-embed-text:latest
```

> [!IMPORTANT]
> Aguarde o download de **cada modelo terminar** antes de rodar o próximo.

Para verificar se foram instalados corretamente:

```bash
ollama list
```

✅ Você deve ver os **três modelos** listados.

---

## 4️⃣ Configurar o Continue

1. No VSCode, abra o painel do **Continue** na barra lateral esquerda
2. Clique em **"Skip and configure manually"**
3. O arquivo `config.yaml` será aberto automaticamente
4. Substitua o conteúdo pelo seguinte:

```yaml
name: Local Config
version: 1.0.0
schema: v1
models:
  - name: Llama 3.1 8B
    provider: ollama
    model: llama3.1:8b
    roles:
      - chat
      - edit
      - apply
  - name: Qwen2.5-Coder 1.5B
    provider: ollama
    model: qwen2.5-coder:1.5b-base
    roles:
      - autocomplete
  - name: Nomic Embed
    provider: ollama
    model: nomic-embed-text:latest
    roles:
      - embed
```

5. Salve o arquivo (<kbd>Ctrl</kbd> + <kbd>S</kbd>)

---

## 5️⃣ Ativar o Tab Autocomplete

1. Vá em **File > Preferences > Settings** (<kbd>Ctrl</kbd> + <kbd>,</kbd>)
2. Pesquise por `Continue`
3. Marque a opção **"Continue: Enable Tab Autocomplete"** ☑️

---

## 🧪 Testando

Abra qualquer arquivo de código (`.py`, `.js`, `.ts`, etc.), comece a digitar e aguarde 1–2 segundos. Um texto cinza (*ghost text*) vai aparecer com a sugestão.

| Tecla | Ação |
|:---:|---|
| <kbd>Tab</kbd> | ✅ **Aceitar** a sugestão |
| <kbd>Esc</kbd> | ❌ **Ignorar** a sugestão |

---

## 📌 Observações

- 🗂️ O autocomplete funciona em todos os arquivos e pastas abertos no VSCode
- 🚫 Por padrão, está **desativado** em arquivos `.txt` e `.md`
- 🦙 O Ollama precisa estar rodando em segundo plano para o autocomplete funcionar
- 🔒 Tudo roda localmente — **nenhum dado é enviado para a internet**

---

## 🛠️ Problemas comuns

<details>
<summary><b>👻 O ghost text não aparece</b></summary>

<br>

- Verifique se o Ollama está rodando: abra o terminal e rode `ollama list`
- Confirme que o **"Enable Tab Autocomplete"** está marcado nas configurações do VSCode

</details>

<details>
<summary><b>🔌 O botão "Connect" fica cinza no painel do Continue</b></summary>

<br>

- Use **"Skip and configure manually"** e edite o `config.yaml` diretamente conforme o **Passo 4**

</details>

---

## 🤝 Contribuindo

Encontrou algo desatualizado ou quer melhorar o tutorial? Abra uma **issue** ou envie um **pull request**! 🚀

<div align="center">

⭐ Se este tutorial te ajudou, deixe uma estrela no repositório!

</div>
