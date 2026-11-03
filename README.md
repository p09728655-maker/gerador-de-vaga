# Gerador de Vagas Patrimar

Aplicativo instalável (PWA) que gera anúncios de vagas no padrão Patrimar:
Instagram (1080×1350), LinkedIn (1200×1200) e status do WhatsApp (1080×1920).
Não tem servidor nem banco de dados: tudo roda no aparelho e funciona sem internet depois do primeiro acesso.

## Publicar
1. Crie um repositório no GitHub e envie estes arquivos na raiz, sem subpastas.
2. Na Vercel, use Add New > Project e importe o repositório. Não há etapa de compilação: mantenha o padrão e clique em Deploy.
3. Abra o endereço gerado (precisa ser https).

## Instalar
- Android (Chrome): menu ⋮ > Instalar aplicativo.
- iPhone (Safari): Compartilhar > Adicionar à Tela de Início.
- Computador (Chrome ou Edge): ícone de instalar na barra de endereço.

## Atualizar
Altere o `index.html` no GitHub. A Vercel publica sozinha, e o aplicativo pega a nova versão ao ser aberto com internet.
Se alterar a lista de arquivos do `sw.js`, troque `vagas-patrimar-v1` por `v2`.

## Trocar logo e foto padrão
Estão embutidas no `index.html`, nas constantes `LOGO_PADRAO` e `FOTO_PADRAO`.

## Arquivos
- `index.html`: o aplicativo
- `manifest.json`: nome, cores e ícones do app
- `sw.js`: funcionamento sem internet
- `icon-192.png` e `icon-512.png`: ícones
