# Focus Invest — Funil de Operações Estruturadas

Funil interativo de captação e qualificação de leads para a campanha de operações
estruturadas (Focus Invest / Focalise).

## Páginas

| Arquivo | Papel |
|---------|-------|
| `index.html` | Página índice — reúne os links de todas as peças |
| `quiz.html` | Quiz de qualificação (7 perguntas → captura de dados → resultado) |
| `agendamento.html` | Fluxo de agendamento (dia → horário → confirmação → passaporte) |

O quiz envia os dados do lead para o agendamento pela URL
(`agendamento.html?n=Nome&w=WhatsApp&e=email&p=perfil`), conectando o funil de ponta a ponta.

É um site estático (HTML/CSS/JS puro, sem build). Funciona em qualquer hospedagem estática.

---

## Publicar no GitHub Pages

### 1. Crie um repositório no GitHub
Acesse https://github.com/new e crie um repositório **público** (ex.: `focus-estruturadas`).
Não marque "Add a README" (este repo já tem um).

### 2. Conecte e envie (rode no terminal, dentro desta pasta)
Troque `SEU-USUARIO` e `focus-estruturadas` pelos seus:

```bash
git remote add origin https://github.com/SEU-USUARIO/focus-estruturadas.git
git push -u origin main
```

### 3. Ative o GitHub Pages
No repositório: **Settings → Pages → Build and deployment**
- **Source:** Deploy from a branch
- **Branch:** `main` / `/ (root)` → **Save**

Em ~1 minuto o site fica no ar em:
`https://SEU-USUARIO.github.io/focus-estruturadas/`

Links diretos:
- Quiz: `https://SEU-USUARIO.github.io/focus-estruturadas/quiz.html`
- Agendamento: `https://SEU-USUARIO.github.io/focus-estruturadas/agendamento.html`

---

## Atualizar o site depois
Edite os arquivos e rode:

```bash
git add -A
git commit -m "Atualiza funil"
git push
```

O Pages republica sozinho a cada push.
