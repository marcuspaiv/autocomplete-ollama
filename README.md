# Autocomplete Gratuito no VSCode com Continue + Ollama

Tutorial completo para configurar autocomplete de código com IA de forma **100% gratuita e offline**, sem precisar de API key ou assinatura.

## O que você vai instalar

| Ferramenta | Função |
|---|---|
| [Continue](https://marketplace.visualstudio.com/items?itemName=Continue.continue) | Extensão do VSCode que gerencia o autocomplete |
| [Ollama](https://ollama.com) | Roda modelos de IA localmente no seu computador |
| qwen2.5-coder | Modelo de IA especializado em código |

---

## Passo 1 — Instalar a extensão Continue no VSCode

1. Abra o VSCode
2. Vá em **Extensions** (`Ctrl+Shift+X`)
3. Pesquise por `Continue`
4. Instale a extensão **"Continue - open-source AI code agent"** (publicada por Continue.dev)

---

## Passo 2 — Instalar o Ollama

1. Acesse [ollama.com](https://ollama.com) e baixe o instalador para o seu sistema operacional
2. Instale normalmente
3. Após instalar, o Ollama ficará rodando em segundo plano em `http://localhost:11434`

---

## Passo 3 — Baixar os modelos

Abra o terminal do VSCode (`Ctrl+`` `) e rode os comandos abaixo um por um:

```bash
ollama pull qwen2.5-coder:1.5b-base
```
> Modelo de autocomplete — leve e rápido

```bash
ollama pull llama3.1:8b
```
> Modelo de chat — cerca de 4.7GB, pode demorar

```bash
ollama pull nomic-embed-text:latest
```
> Modelo de embeddings — usado para busca no código

Aguarde o download de cada um terminar antes de rodar o próximo.

Para verificar se foram instalados corretamente:

```bash
ollama list
```

Você deve ver os três modelos listados.

---

## Passo 4 — Configurar o Continue

1. No VSCode, abra o painel do Continue na barra lateral esquerda
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

5. Salve o arquivo (`Ctrl+S`)

---

## Passo 5 — Ativar o Tab Autocomplete

1. Vá em **File > Preferences > Settings** (`Ctrl+,`)
2. Pesquise por `Continue`
3. Marque a opção **"Continue: Enable Tab Autocomplete"**

---

## Testando

Abra qualquer arquivo de código (`.py`, `.js`, `.ts`, etc.), comece a digitar e aguarde 1-2 segundos. Um texto cinza (ghost text) vai aparecer com a sugestão.

- Pressione `Tab` para **aceitar** a sugestão
- Pressione `Esc` para **ignorar**

---

## Observações

- O autocomplete funciona em todos os arquivos e pastas abertos no VSCode
- Por padrão, está desativado em arquivos `.txt` e `.md`
- O Ollama precisa estar rodando em segundo plano para o autocomplete funcionar (ele inicia automaticamente com o Windows)
- Tudo roda localmente — nenhum dado é enviado para a internet

---

## Problemas comuns

**O ghost text não aparece**
- Verifique se o Ollama está rodando: abra o terminal e rode `ollama list`
- Confirme que o "Enable Tab Autocomplete" está marcado nas configurações do VSCode

**O botão "Connect" fica cinza no painel do Continue**
- Use "Skip and configure manually" e edite o `config.yaml` diretamente conforme o Passo 4

---

## Contribuindo

Encontrou algo desatualizado ou quer melhorar o tutorial? Abra uma issue ou envie um pull request!
