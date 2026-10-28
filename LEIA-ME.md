# Torre da Disciplina: como colocar no ar de graça

Você vai usar dois serviços gratuitos:
- **Firebase** (Google): login com Google ou e-mail e o banco de dados que salva os heróis.
- **GitHub Pages**: hospeda o site e dá um endereço público, como `seunome.github.io/torre`.

Tudo pode ser feito pelo navegador, inclusive no celular, mas no computador é mais confortável.

## 1. Criar o projeto no Firebase
1. Acesse https://console.firebase.google.com e entre com sua conta Google.
2. Toque em **Criar projeto**, dê o nome `torre-da-disciplina` e conclua. O Google Analytics pode ficar desligado.
3. Na tela do projeto, toque no ícone **</>** (Web) para registrar um app. Dê o nome `site`. Não marque Firebase Hosting.
4. Vai aparecer um bloco `firebaseConfig` com `apiKey`, `authDomain` e outros campos. Copie esses valores.

## 2. Ligar o login
1. No menu, vá em **Authentication** e toque em **Vamos começar**.
2. Em **Método de login**, ative **Google** (escolha seu e-mail de suporte) e salve.
3. Ative também **E-mail/senha** e salve.

## 3. Criar o banco de dados
1. No menu, vá em **Firestore Database** e toque em **Criar banco de dados**.
2. Escolha a região `southamerica-east1 (São Paulo)` e o **modo de produção**.
3. Abra a aba **Regras**, apague o conteúdo e cole o conteúdo do arquivo `firestore.rules`. Toque em **Publicar**.
   As regras já trazem o seu e-mail como conta Master. Só essa conta consegue alterar o jogo.

## 4. Preencher o config.js
Abra o arquivo `config.js` e troque cada `COLE_AQUI` pelo valor correspondente do passo 1.4. Mantenha as aspas.

## 5. Publicar no GitHub Pages
1. Crie uma conta em https://github.com (grátis).
2. Toque em **+** e **New repository**. Nome: `torre`. Deixe **Public**. Crie.
3. Toque em **uploading an existing file** e envie estes arquivos: `index.html`, `config.js`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png`. Toque em **Commit changes**.
   Não envie `firestore.rules` nem este `LEIA-ME.md`: o repositório é público e eles não são necessários no site.
4. Vá em **Settings > Pages**. Em **Branch**, escolha `main` e a pasta `/ (root)`. Salve.
5. Em alguns minutos o site fica no ar em `https://SEU-USUARIO.github.io/torre/`.

## 6. Autorizar o endereço do site no Firebase
Sem isso o login com Google não funciona.
1. No Firebase, vá em **Authentication > Configurações > Domínios autorizados**.
2. Toque em **Adicionar domínio** e coloque `SEU-USUARIO.github.io` (sem `https://` e sem `/torre`).

## 7. Instalar no celular
- **Android (Chrome):** abra o site, menu ⋮ e **Adicionar à tela inicial** (ou **Instalar app**).
- **iPhone (Safari):** abra o site, botão Compartilhar e **Adicionar à Tela de Início**.

O ícone abre o jogo em tela cheia, como um app.

## Para atualizar o jogo depois
Envie o novo `index.html` no mesmo repositório (Add file > Upload files). Não envie um `config.js` novo, senão perde a configuração.

## Painel Master
Entre no site com a conta Google **kaiovslima@gmail.com**. Uma aba **Master** aparece no menu de baixo só para você. Nela você pode:
- **Eventos:** criar eventos com data de início e fim que multiplicam XP, ouro e farm offline. Tem um modelo pronto de Halloween. Durante o evento os monstros da torre podem ganhar outro nome e uma imagem PNG.
- **Presentes:** dar XP e ouro que cada jogador coleta uma vez na aba Hoje.
- **Itens:** criar e editar itens, com ícone PNG, requisitos, classe, preço e disponibilidade (sempre, só durante um evento ou entre datas). Itens de tempo limitado aparecem numa aba própria da loja.
- **Árvores:** editar habilidades ou criar novas em qualquer nível de cada classe.
- **Missões:** editar ou criar missões diárias e semanais, inclusive só para eventos.
- **Geral:** dificuldade da torre, recompensa offline, limites de missões, preço de venda e um aviso para todos.

As imagens devem ser PNG em pixel art. Imagens maiores que 32×32 são reduzidas automaticamente.

## Trocar a conta Master
1. Em `firestore.rules`, troque `kaiovslima@gmail.com` pelo novo e-mail e publique as regras de novo no Firebase.
2. Entre no site com a nova conta, abra a aba **Guilda** e toque em **Código Master desta conta**. Copie o código.
3. Em `config.js`, troque o valor de `masterHash` por esse código e envie o arquivo de novo no GitHub.

## Limites do plano grátis
O plano Spark do Firebase não pede cartão. O Firestore grátis permite 20 mil gravações e 50 mil leituras por dia, o que sobra para você e um grupo de amigos.

## Se algo der errado
- **"Este site ainda não foi autorizado"**: faltou o passo 6.
- **"Esse tipo de login não foi ativado"**: faltou o passo 2.
- **Ponto vermelho ao lado do nome / erro ao sincronizar**: confira as regras do passo 3.
- **Jogo funciona mas sem login**: o `config.js` ainda tem `COLE_AQUI`.
