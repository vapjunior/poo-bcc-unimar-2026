# Publicar este material no GitHub Pages

Este repositório foi adaptado para funcionar como site estático no GitHub Pages. A página inicial é `index.html`, e cada unidade continua como uma apresentação Reveal.js em um arquivo HTML separado.

## Estrutura atual

- `index.html`: menu inicial do curso.
- `unidade_1_paradigmas_poo_reveal(1).html`: Unidade 1.
- `poo_unidade2_php84_tipos_reveal.html`: Unidade 2.
- `unidade_3_modelo_objetos_classes_instancias_reveal_slides7_8_ajustados.html`: Unidade 3.
- `.nojekyll`: instrui o GitHub Pages a publicar os arquivos exatamente como estão.

## Testar localmente

Na pasta do projeto, execute:

```bash
python3 -m http.server 8000
```

Depois acesse:

```text
http://localhost:8000
```

Confira se o menu inicial abre as unidades e se o botão `Menu` dentro dos slides volta para a página inicial.

## Criar o repositório no GitHub

1. Acesse <https://github.com/new>.
2. Defina um nome para o repositório, por exemplo `poo-php`.
3. Escolha `Public` se quiser usar GitHub Pages gratuito em um repositório público.
4. Não marque opções de criação automática como README, `.gitignore` ou license se você for enviar esta pasta local diretamente.
5. Clique em `Create repository`.

## Enviar os arquivos locais

Na pasta deste projeto, execute os comandos abaixo. Troque `SEU_USUARIO` e `poo-php` pelos dados reais do seu GitHub.

```bash
git init
git add .
git commit -m "Publica material de POO em PHP"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/poo-php.git
git push -u origin main
```

Se o repositório local já tiver Git inicializado, use apenas:

```bash
git add .
git commit -m "Adapta site para GitHub Pages"
git push
```

## Ativar o GitHub Pages

1. Abra o repositório no GitHub.
2. Entre em `Settings`.
3. No menu lateral, clique em `Pages`.
4. Em `Build and deployment`, selecione:
   - `Source`: `Deploy from a branch`
   - `Branch`: `main`
   - Pasta: `/ (root)`
5. Clique em `Save`.

Depois de alguns minutos, o GitHub exibirá a URL publicada. Ela terá um formato parecido com:

```text
https://SEU_USUARIO.github.io/poo-php/
```

## Atualizar o conteúdo depois

Sempre que criar novas unidades:

1. Adicione o novo arquivo HTML na raiz do projeto.
2. Edite `index.html` e inclua um novo card no menu.
3. Adicione no novo HTML um link de retorno para `index.html`, seguindo o padrao dos arquivos atuais.
4. Envie as mudancas:

```bash
git add .
git commit -m "Adiciona nova unidade"
git push
```

O GitHub Pages atualiza o site automaticamente após o push.

## Observações importantes

- O GitHub Pages não executa PHP no servidor. Ele publica HTML, CSS, JavaScript e arquivos estáticos.
- Neste projeto, as unidades já estão em HTML e continuam funcionando sem backend.
- As bibliotecas Reveal.js são carregadas por CDN. Para apresentar sem internet, será necessário baixar essas dependências e ajustar os links para arquivos locais.
