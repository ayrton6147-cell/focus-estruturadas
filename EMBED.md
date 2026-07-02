# Como publicar e integrar o quiz na Focus Invest

Quiz interativo de operações estruturadas que, ao final, gera uma **análise
aprofundada e personalizada** para o lead (relatório na tela + PDF + WhatsApp).
Site estático (HTML/CSS/JS puro, sem build).

## Arquivos

| Arquivo | Papel |
|---------|-------|
| `index.html` | **O quiz** — página de entrada (o link é este) |
| `relatorio.html` | Análise aprofundada entregue ao lead (aberta pelo quiz) |
| `assets/logo-focus.png` | Logo (branco, para fundo escuro) |
| `agendamento.html` | Fluxo de agendamento (preservado, fora do fluxo principal) |

## 1. Publicar no servidor da Focus

Suba a pasta inteira para o servidor (ex.: `https://focusinvestimentos.com/quiz-estruturadas/`).
Como o entry é `index.html`, o link direto já abre o quiz:

```
https://focusinvestimentos.com/quiz-estruturadas/
```

## 2. Embutir numa Landing Page (Elementor / WordPress)

Widget **HTML**, com auto-resize (o quiz reporta a altura ao container):

```html
<div style="max-width:680px;margin:0 auto;">
  <iframe id="focusQuiz"
    src="https://focusinvestimentos.com/quiz-estruturadas/"
    style="width:100%;border:0;display:block;min-height:640px;overflow:hidden;background:transparent;"
    scrolling="no" loading="lazy" title="Quiz — Operações Estruturadas Focus"></iframe>
</div>
<script>
(function(){
  var f=document.getElementById('focusQuiz');
  window.addEventListener('message',function(e){
    if(e.data && e.data.focusFunil==='height' && e.data.height){ f.style.height=(e.data.height+10)+'px'; }
  });
})();
</script>
```
> Ajuste a verificação de origem (`e.origin`) para o domínio final, por segurança.

## 3. Integrar com o RD Station (CRM)

Quando o lead é capturado (após o consentimento LGPD), o quiz chama uma única
função **`captureLead(payload)`** e dispara:
- um evento DOM `focus:lead` (`window.addEventListener('focus:lead', ...)`)
- um push no `window.dataLayer` (`event: 'focus_lead'`) para GTM

O `payload` já vem pronto:

```json
{
  "nome": "...", "whatsapp": "...", "consentimento_lgpd": true,
  "perfil": "prioritario|qualificado|aquecendo|construcao",
  "arquetipo": "O Construtor Protegido",
  "dor": "protecao", "score": 92,
  "ticket": "R$ 150–500 mil", "timing": "imediato",
  "patrimonio": "R$ 100–500 mil", "origem": "quiz_estruturadas"
}
```

Para conectar o RD Station, edite **um único ponto** em `index.html` — a função
`captureLead()` (bloco comentado "PONTO DE INTEGRAÇÃO — CRM / RD STATION"). Opções:
- **RD Station Conversions API / Forms** (recomendado) — envie o `payload`.
- **Webhook** (`fetch('SEU_WEBHOOK_RD', {method:'POST', body: JSON.stringify(payload)})`).
- **GTM** — capture o evento `focus_lead` do dataLayer e dispare a tag do RD.

O RD Station passa então a ser a fonte de verdade e pode automatizar o envio da
análise ao WhatsApp do lead.

## Atualizar depois
Edite os arquivos e re-suba para o servidor (ou `git push`, se em Pages).
