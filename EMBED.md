# Como embutir o funil na Landing Page (WordPress / Elementor)

O funil é um site estático hospedado no GitHub Pages. Para colocá-lo na LP da
campanha (ex.: antes do vídeo, para qualificar o lead), basta um iframe que se
ajusta sozinho à altura do conteúdo.

## Passo a passo no Elementor

1. Edite a página da campanha no Elementor.
2. Arraste um widget **HTML** para o ponto onde o quiz deve aparecer (ex.: acima do vídeo).
3. Cole o código abaixo.
4. Clique em **Atualizar / Publicar**.

## Código do embed

```html
<div style="max-width:680px;margin:0 auto;">
  <iframe id="focusFunilFrame"
    src="https://ayrton6147-cell.github.io/focus-estruturadas/quiz.html"
    style="width:100%;border:0;display:block;min-height:620px;overflow:hidden;background:transparent;"
    scrolling="no" loading="lazy" title="Quiz Focus Invest — Operações Estruturadas"></iframe>
</div>
<script>
(function(){
  var f = document.getElementById('focusFunilFrame');
  window.addEventListener('message', function(e){
    if (e.origin !== 'https://ayrton6147-cell.github.io') return;
    if (e.data && e.data.focusFunil === 'height' && e.data.height) {
      f.style.height = (e.data.height + 10) + 'px';
    }
  });
})();
</script>
```

### Como funciona
- O iframe carrega o **quiz** (entrada do funil). Quando o lead se qualifica e clica
  em "Agendar conversa gratuita", o próprio iframe avança para o **agendamento**,
  já com os dados do lead — tudo dentro do mesmo embed.
- O script de auto-resize ajusta a altura do iframe conforme a tela muda
  (pergunta → resultado → agendamento → passaporte), sem barra de rolagem interna.
- A verificação `e.origin` garante que só a página do funil controla a altura.

## Atualizar o conteúdo depois
Edite os arquivos localmente e rode, dentro da pasta do projeto:

```bash
git add -A
git commit -m "Atualiza funil"
git push
```

O GitHub Pages republica sozinho em ~1 minuto e a LP reflete a mudança
(sem mexer no Elementor).
