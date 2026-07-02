# Focus Invest — Quiz de Operações Estruturadas

Quiz interativo de qualificação que, ao final, entrega ao lead uma **análise
aprofundada e personalizada** (relatório na tela + PDF + WhatsApp).

Identidade visual Focus: navy `#123245`, dourado `#bfa174`, branco, fonte Poppins,
logo Focus. Site estático (HTML/CSS/JS puro, sem build) — funciona em qualquer
hospedagem estática.

## Estrutura

| Arquivo | Papel |
|---------|-------|
| `index.html` | **O quiz** (entrada — o link é este) |
| `relatorio.html` | Análise aprofundada entregue ao lead |
| `assets/logo-focus.png` | Logo Focus (branco) |
| `agendamento.html` | Fluxo de agendamento (preservado, fora do fluxo atual) |

## Fluxo

1. Lead responde 8 toques (perfil + como pensa).
2. Vê o resultado (arquétipo + medidores) e, após o consentimento LGPD, libera a
   recomendação e informa o WhatsApp.
3. Recebe a **análise completa** (`relatorio.html`): perfil, estruturas
   recomendadas, cenários e próximos passos — com **baixar PDF** e **WhatsApp**
   do time da Focus (5551 95107857).

## Publicação e integração

Ver **[EMBED.md](EMBED.md)** — como subir no servidor da Focus, embutir por iframe
na LP (Elementor) e **integrar o RD Station** (ponto único `captureLead()` +
evento `focus:lead` + `dataLayer`).

## Conformidade

- Rodapé institucional com CNPJ, Resolução CVM 178/23 e disclaimer XP em todas as páginas.
- Consentimento LGPD explícito e obrigatório na captura.
- Sem promessa de retorno; disclaimers de risco presentes.
