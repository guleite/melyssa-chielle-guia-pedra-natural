# Guia Pedra Natural · Melyssa Chielle

Landing page de captação para o download gratuito do **Guia visual de uso de pedras naturais em projetos de arquitetura**, da Melyssa Chielle Arquitetura & Interiores. Proposta de layout da Concept Agência.

**Site:** https://guleite.github.io/melyssa-chielle-guia-pedra-natural/

## O que a página faz

- Hero com livro 3D interativo e projeto da arquiteta (Casa Ametista).
- Livro que folheia com a rolagem, com páginas reais do guia.
- Pop-up de formulário (nome, e-mail, WhatsApp e consentimento LGPD) aberto por todos os botões de download. O exemplar 3D se abre conforme os campos são preenchidos e mostra o nome da pessoa na folha de rosto.
- Formulário também na seção final da página.
- Página de agradecimento (`#obrigado`) com download do PDF.
- Eventos para Google Tag Manager / GA4 no `dataLayer`.

## Estrutura

```
index.html            página completa (HTML, CSS e JS no mesmo arquivo)
favicon.svg           monograma MC
img/guia/             páginas do guia renderizadas (pNN.jpg)
img/mockups/          mockups do livro
img/*.webp            fotos da arquiteta e dos projetos
guia/                 PDF do guia (25 páginas)
```

## Antes de colocar em produção

1. **Google Tag Manager:** no topo do `index.html`, troque `GTM-XXXXXXX` pelo ID do contêiner e remova os comentários do snippet e do `<noscript>`. Eventos enviados: `cta_click`, `form_open`, `form_start`, `form_error`, `generate_lead`, `virtual_page_view`, `file_download`, `guide_preview_complete`. Marque `generate_lead` e `file_download` como eventos-chave no GA4.
2. **Envio dos leads:** a função `sendLead()` no `index.html` é o ponto de integração com o CRM ou a automação de e-mail (RD Station, HubSpot, webhook). Hoje ela não envia os dados para lugar nenhum.
3. **Política de privacidade:** o texto do pop-up é um texto-base e deve ser revisado pela assessoria jurídica do escritório.
4. **PDF protegido:** nesta versão de apresentação o PDF fica em `guia/` e pode ser acessado diretamente pelo endereço. Em produção, vale servir o arquivo somente após o cadastro (por exemplo, link enviado por e-mail ou URL assinada).
