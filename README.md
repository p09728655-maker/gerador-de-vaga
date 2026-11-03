# Gerador de Vagas Patrimar

Aplicativo instalável (PWA) que gera anúncios de vagas no padrão Patrimar:
Instagram (1080×1350), LinkedIn (1200×1200) e status do WhatsApp (1080×1920).
Não tem servidor nem banco de dados: tudo roda no aparelho e funciona sem internet depois do primeiro acesso.

## Publicar
1. Crie um repositório no GitHub e envie estes arquivos na raiz, sem subpastas.
2. Na Vercel, use Add New > Project e importe o repositório. Não há etapa de compilação: mantenha o padrão e clique em Deploy.
3. Abra o endereço gerado (precisa ser https).

## Instalar
Use o botão **Instalar aplicativo**, no topo da tela.
- Chrome e Edge (Android e computador): abre o pedido de instalação do próprio navegador.
- iPhone e iPad: mostra o passo a passo (Compartilhar > Adicionar à Tela de Início).
- Navegador de dentro do Instagram, Facebook ou LinkedIn: orienta a abrir no Safari ou no Chrome, porque ali não instala.
- O botão some quando o app já está aberto instalado.

## Salvar a arte
O arquivo sai com o nome da vaga e a rede, por exemplo `Operador de Fresadora - Instagram.png`.
No Chrome e no Edge do computador, abre a janela "Salvar como" com esse nome já preenchido. O navegador lembra a última pasta usada.
No celular, abre o compartilhar do aparelho (WhatsApp, Instagram, Salvar imagem).

## Controle de versão
A versão fica em um lugar só: a constante `VERSAO`, no `index.html`. Ela aparece no rodapé do formulário.
Ao publicar uma mudança, aumente a versão (ex.: `1.1.0` → `1.2.0`). O `sw.js` lê esse número e renova a cópia offline sozinho. Não é preciso editar o `sw.js`.

### Histórico
- **1.1.0**: logomarca original no lugar do print desfocado; ícone novo (P e estrela da marca sobre fundo vermelho); botão Instalar aplicativo; tela do computador sem rolagem; arquivo salvo com o nome da vaga; versão visível no app.
- **1.0.0**: versão inicial.

## Trocar logo e foto padrão
Estão embutidas no `index.html`, nas constantes `LOGO_PADRAO` e `FOTO_PADRAO`.
A logo padrão e os ícones foram gerados a partir do arquivo `Logotipo Patrimar.jpg`.

## Arquivos
- `index.html`: o aplicativo
- `manifest.json`: nome, cores, ícones e capturas da janela de instalação
- `sw.js`: funcionamento sem internet
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` (Android) e `apple-touch-icon.png` (iPhone): ícones
- `screenshot-celular.webp` e `screenshot-computador.webp`: imagens mostradas na janela de instalação do Chrome. Se a tela mudar muito, gere de novo.
- `Logotipo Patrimar.jpg`: logomarca original, fonte da logo e dos ícones
