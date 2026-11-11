# Gerador de Vagas Patrimar

Aplicativo instalável (PWA) com duas abas, no topo da tela:
- **Vagas**: anúncios de vagas para Instagram (1080×1350), LinkedIn (1200×1200) e status do WhatsApp (1080×1920).
- **Convites**: convites de reunião, treinamento, evento, aniversário e aniversariantes do mês (ver [Convites](#convites)).

Não tem servidor nem banco de dados: tudo roda no aparelho e funciona sem internet depois do primeiro acesso.
A única exceção é o botão opcional **Gerar com IA**, que precisa de internet e de uma chave da API do Claude.

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
Cada arquivo sai com o nome da vaga e a rede, por exemplo `Operador de Fresadora - Instagram.png`. Salvar de novo a mesma vaga na mesma pasta substitui o arquivo.
- **Salvar as 3 artes** (botão principal): gera Instagram, LinkedIn e status do WhatsApp de uma vez.
  - Computador (Chrome e Edge), **app instalado**: na primeira vez, escolha ou crie uma pasta (ex.: `Vagas`). As próximas vão direto para ela, sem perguntar; **Trocar pasta** aparece na mensagem.
  - Cada vaga ganha uma pasta com o nome do cargo dentro da pasta escolhida: `Vagas › Operador de CNC › Operador de CNC - Instagram.png`. Salvar de novo a mesma vaga substitui os arquivos dela. Vale também na aba do navegador. No celular e no download comum não há pasta da vaga. O navegador pode pedir permissão para editar a pasta; escolha "Permitir em todas as visitas".
  - O navegador não aceita a raiz de Downloads, Documentos ou Área de Trabalho: crie uma pasta dentro delas.
  - Computador, **aba do navegador**: pergunta a pasta a cada vez, já abrindo na última usada. A pasta só fica guardada no app instalado, que sempre roda num perfil normal do navegador.
  - Celular: abre o compartilhar com as 3 imagens (Salvar imagens, WhatsApp, Drive).
  - Outros navegadores: baixa os 3 arquivos (o navegador pode pedir para permitir vários downloads).
  - Se o texto não couber em algum formato, a mensagem avisa qual conferir.
- **Só Instagram / Só LinkedIn / Só WhatsApp**: salva apenas a arte da aba aberta, como antes (janela "Salvar como" no computador; compartilhar no celular).
- **Copiar legenda**: copia o texto do post, montado com os campos preenchidos (chamada e cargo, cidade, requisitos, diferencial, atividades, benefícios e contato) e hashtags. É só colar no Instagram, LinkedIn ou WhatsApp. Se o navegador não deixar copiar sozinho, abre uma janela com o texto selecionado.
  - Hashtags: as fixas da constante `HASHTAGS` no `index.html` (`#vagas #emprego #vagasdeemprego #trabalheconosco #industriamoveleira #patrimarmoveis`), mais a do cargo (`#operadordecnc`, sem nível nem turno) e a da cidade (`#vagasjaci`), geradas dos campos.

## Convites
Aba **Convites**, no topo da tela. Tem formulário, prévia e botões de salvar próprios; a aba Vagas não muda.
- **Tipos:** Reunião, Treinamento, Evento, Aniversário e Aniversariantes do mês. Cada tipo mostra só os campos dele e guarda o próprio texto neste navegador: trocar de tipo não apaga o que foi digitado no outro.
- **Formatos:** Post 4:5 (1080×1350, para WhatsApp e e-mail), Status 9:16 (1080×1920) e Mural A4 (1240×1754, A4 a 150 dpi, para imprimir e afixar). No status, topo e rodapé têm folga porque o WhatsApp cobre essas faixas.
- **Reunião, Treinamento e Evento:** chamada, assunto, para quem, data, horário de início e término, local, pauta (um item por linha) e observação (ex.: confirmar presença).
- **Aniversário:** nome, setor, data, mensagem e foto opcional. A foto **não** fica salva no navegador, para não aparecer por engano no cartão seguinte; ao recarregar a página, envie de novo.
- **Aniversariantes do mês:** uma pessoa por linha, `dia - nome - setor` (ex.: `05 - Maria da Silva - Montagem`). Pode colar direto do Excel (colunas separadas por tabulação); a data pode vir como `05`, `05/11` ou `05/11/1990` (vale só o dia), e a linha de cabeçalho é ignorada. A lista sai em ordem de dia; com mais de 7 pessoas, em 2 colunas. Data, horário e local da comemoração são opcionais.
- **Texto que não cabe:** a arte diminui tudo junto até caber. Se a letra ficar abaixo de 70% do tamanho normal, aparece o aviso; com muitos aniversariantes, prefira o Status ou o Mural.
- **Salvar:** igual à vaga (Salvar as 3 artes, Só [formato], Copiar texto), com pasta própria: no app instalado, a pasta escolhida para convites é lembrada separada da de vagas. Cada convite ganha uma pasta com o nome dele.
- **Nome do arquivo:** título + data, para a reunião desta semana não substituir a da semana passada. Ex.: `Reunião de resultados - 13-11-2026 - Post.png`, `Aniversário Maria da Silva - Mural A4.png`.
- **Copiar texto:** monta a mensagem com data por extenso, horário, local e pauta, com emojis, para mandar junto com a arte no WhatsApp ou no e-mail.
- **Adicionar à agenda:** botão em "Quando e onde" (Reunião, Treinamento, Evento e comemoração dos Aniversariantes). Gera um arquivo `.ics` com título, data, horário, local, pauta e lembrete 30 minutos antes, que o Outlook, o Google Agenda e o celular abrem como compromisso.
  - **O que ele não faz:** não envia convite nem colhe confirmação de presença. Para isso, quem organiza abre o arquivo no Outlook e convida os participantes por lá. Também dá para anexar o arquivo no e-mail ou no WhatsApp.
  - **Regras:** sem término, o compromisso fica com 1 hora. Término antes do início (ex.: 20h às 1h) termina no dia seguinte. Sem horário, vira compromisso de dia inteiro. A mensagem ao lado do botão avisa qual regra foi usada.
  - **Horário:** gravado em UTC a partir do fuso do computador que gerou o arquivo. O relógio desse computador precisa estar no fuso da fábrica.
  - **Mesmo convite, mesmo identificador** (tipo + título + data): mudar só o horário e mandar de novo tende a atualizar o compromisso em vez de duplicar, mas isso depende do calendário de quem recebe. Mudou o dia: é um compromisso novo; peça para apagarem o antigo.
  - **Google Agenda no computador:** o arquivo não abre sozinho; use Configurações › Importar e exportar › Importar.
- **Logomarca:** a mesma da aba Vagas (Enviar logomarca, na aba Vagas, vale para as duas).
- **Abrir direto numa aba:** a última aba usada é lembrada. O endereço com `#vagas` ou `#convites` abre direto nela; no app instalado, clique com o botão direito no ícone para escolher.
- **Mudar textos de exemplo ou incluir um tipo:** constante `TIPOS_CV` no `index.html` (o ícone novo vai em `ICONES`).

## Sugestão de conteúdo por cargo
Ao digitar o **Cargo**, o app preenche Requisitos, Diferencial e Principais atividades.
- **Lista de cargos:** clicar no campo ou na seta mostra todos os cargos, com o atual marcado, mesmo com o campo preenchido. Digitar filtra pelo começo de cada palavra (`op emp` acha `Operador de Empilhadeira`). Funciona com mouse, toque e teclado (setas, Enter e Esc).
- **De onde vem o texto:** primeiro, o último anúncio salvo neste navegador para aquele cargo; se não houver, o modelo padrão (constante `MODELOS`, no `index.html`).
- **Aprende com o uso:** ao clicar em Salvar PNG, o texto da vaga vira o modelo do cargo neste navegador. Cargo novo entra na lista. Guarda até 80 cargos.
- **Não apaga o que foi digitado:** só preenche sozinho se os campos estiverem vazios ou com um modelo. Se houver texto próprio, mostra o botão **Usar modelo**. Depois de preencher, **Desfazer** volta ao texto anterior.
- **Mesmo cargo escrito de outro jeito:** preenche sozinho, como se fosse igual. O app ignora maiúscula, acento, "(a)", feminino, plural, "de/da/do", nível (I, II, Jr, Pleno, Sênior) e turno, e troca sinônimos (ajudante = auxiliar, op. = operador, téc. = técnico). Ex.: `Operadora CNC II`, `Op. de CNC` e `operador(a) de cnc` acham `Operador de CNC`; `Ajudante de Produção - 2º turno` acha `Auxiliar de Produção`. Para incluir um sinônimo, edite `SINONIMOS` no `index.html`.
- **Cargo parecido:** não preenche sozinho. Quando a pessoa para de digitar, mostra "o mais parecido é..." com o botão **Usar modelo**. Vale para erro de digitação (`Secionadora` → `Seccionadora`), palavra a mais ou a menos (`Operador de Coladeira` → `Operador de Coladeira de Borda`) e cargo que só existe dentro de um modelo (`Mecânico` → `Mecânico de Manutenção`). Cargo de outra máquina ou área não é oferecido: `Operador de Lixadeira` não puxa o de Fresadora, e `Operador` sozinho não puxa nada.
- Os modelos padrão são genéricos: o RH deve revisar antes de publicar. Para mudar ou incluir um cargo para todos, edite `MODELOS` e publique uma versão nova.
- **Levar para outro computador:** os modelos aprendidos ficam no navegador onde a vaga foi salva. Para passar para outro, use **Modelos salvos** (embaixo do formulário) → **Exportar arquivo**, e no outro computador **Modelos salvos** → **Importar arquivo**. A importação junta os modelos: cargo novo entra; quando o mesmo cargo existe nos dois, fica o texto salvo por último. Para um modelo valer para todos sem importar, mande o arquivo para quem cuida do app incluir em `MODELOS`.

## Gerar com IA (Claude)
O botão **Gerar com IA**, no bloco Conteúdo, escreve Requisitos, Diferencial e Principais atividades a partir do **Cargo**.
- **Onde colocar a chave:** botão **Configurar IA**, embaixo do formulário. Cole a chave (`sk-ant-...`) e clique em **Salvar e testar**. O teste consulta o modelo na Anthropic, sem custo; chave recusada não é salva.
- **Onde a chave fica:** só no navegador onde foi colada (localStorage). Não vai para o GitHub nem para a Vercel. Outro computador precisa colar de novo. **Remover chave** apaga.
- **Risco:** quem usa aquele computador consegue ler a chave pelas ferramentas do navegador. Não salve em computador compartilhado. Crie uma chave só para este app em console.anthropic.com e defina um limite de gasto na conta.
- **Como entra o texto:** igual ao modelo por cargo. Aparece **Desfazer** para voltar ao texto anterior e, ao salvar a arte, o texto vira o modelo daquele cargo neste navegador. O RH revisa antes de publicar.
- **Modelo:** `claude-opus-5-5`, esforço baixo, resposta em formato fixo (JSON). Se o modelo recusar o pedido, a Anthropic tenta de novo com outro modelo (parâmetro `fallbacks`). Para trocar o modelo, mude a constante `MODELO` no `index.html`.
- **Custo:** cobrado por uso na conta da Anthropic. Cada geração usa poucos milhares de tokens; acompanhe o gasto real no console.
- **Regras do texto:** ficam na constante `SISTEMA` (tamanho dos itens, não inventar salário ou benefício, NR só quando exigida por lei). Usa três modelos de `MODELOS` como exemplo de tom.

### Atualizar o SDK
O arquivo `anthropic-sdk.js` é o SDK oficial da Anthropic (`@anthropic-ai/sdk`) empacotado num arquivo só, porque o app não tem etapa de compilação. Ele só é baixado no primeiro clique em Gerar com IA. Não edite à mão. Para trocar a versão, numa pasta fora do repositório:
```bash
npm install @anthropic-ai/sdk@<versão> esbuild
echo 'export { default } from "@anthropic-ai/sdk";' > entrada.mjs
npx esbuild entrada.mjs --bundle --format=esm --platform=browser --minify --target=es2020 --outfile=anthropic-sdk.js
```
Copie o `anthropic-sdk.js` gerado para o repositório, mantendo o comentário de licença do topo com a versão nova, e aumente a `VERSAO`.

## Controle de versão
A versão fica em um lugar só: a constante `VERSAO`, no `index.html`. Ela aparece no rodapé do formulário.
Ao publicar uma mudança, aumente a versão (ex.: `1.1.0` → `1.2.0`). O `sw.js` lê esse número e renova a cópia offline sozinho. Não é preciso editar o `sw.js`.

### Histórico
- **1.7.3**: a janela de pasta que não abre agora é reconhecida pelo foco do app (o app perde o foco quando a janela aparece), não só pelo tempo; a nova tentativa começa em Downloads, que é onde o Salvar como funciona; a mensagem de cancelamento ganhou o botão Baixar em Downloads.
- **1.7.2**: quando a janela de pasta ou de Salvar como volta "cancelada" em menos de 1 segundo (o Chrome não conseguiu abrir, ninguém cancelou), o app tenta de novo sem o local de partida guardado e passa a abrir assim neste navegador; se ainda não abrir, baixa as artes na pasta Downloads em vez de parar.
- **1.7.1**: "Salvamento cancelado" só aparece quando a janela foi fechada ou o acesso negado, e diz como salvar; falha ao gravar o arquivo (arte aberta em outro programa, antivírus) mostra o motivo em vez de "cancelado"; no Só [formato], se não gravar no local escolhido, baixa na pasta Downloads.
- **1.7.0**: botão Adicionar à agenda nos convites (arquivo `.ics` para Outlook, Google Agenda e celular, com lembrete 30 minutos antes).
- **1.6.0**: aba Convites (reunião, treinamento, evento, aniversário e aniversariantes do mês) com artes de post, status e mural A4, texto para copiar e pasta própria; abas Vagas e Convites no topo, com a última aberta lembrada.
- **1.5.1**: Salvar as 3 artes cria uma pasta com o nome da vaga dentro da pasta escolhida.
- **1.5.0**: botão Salvar as 3 artes (pasta lembrada no app instalado; compartilhar as 3 no celular); botão Copiar legenda com hashtags geradas do cargo e da cidade; aviso de texto que não coube em algum formato.
- **1.4.1**: a lista de cargos mostra todos ao clicar no campo, mesmo com um cargo já preenchido (antes era preciso apagar o campo).
- **1.4.0**: busca de cargo tolerante (feminino, plural, nível, turno, sinônimos e erro de digitação) e oferta do modelo mais parecido; botão Modelos salvos para exportar e importar os modelos aprendidos entre computadores.
- **1.3.0**: botão Configurar IA para guardar a chave da API do Claude neste navegador; botão Gerar com IA, que escreve Requisitos, Diferencial e Principais atividades a partir do cargo.
- **1.2.0**: sugestão de Requisitos, Diferencial e Principais atividades ao digitar o cargo; 20 modelos padrão; o app aprende com cada vaga salva.
- **1.1.0**: logomarca original no lugar do print desfocado; ícone novo (P e estrela da marca sobre fundo vermelho); botão Instalar aplicativo; tela do computador sem rolagem; arquivo salvo com o nome da vaga; versão visível no app.
- **1.0.0**: versão inicial.

## Trocar logo e foto padrão
Estão embutidas no `index.html`, nas constantes `LOGO_PADRAO` e `FOTO_PADRAO`.
A logo padrão e os ícones foram gerados a partir do arquivo `Logotipo Patrimar.jpg`.

## Arquivos
- `index.html`: o aplicativo
- `manifest.json`: nome, cores, ícones e capturas da janela de instalação
- `sw.js`: funcionamento sem internet
- `anthropic-sdk.js`: SDK oficial da Anthropic, usado só pelo botão Gerar com IA
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` (Android) e `apple-touch-icon.png` (iPhone): ícones
- `screenshot-celular.webp` e `screenshot-computador.webp`: imagens mostradas na janela de instalação do Chrome. Se a tela mudar muito, gere de novo.
- `Logotipo Patrimar.jpg`: logomarca original, fonte da logo e dos ícones
