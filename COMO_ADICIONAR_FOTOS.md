# Como adicionar fotos ao site

## Criar um álbum novo

1. Crie uma pasta dentro de `images/`:
   ```
   mkdir images/nome-do-album
   ```

2. Adicione um bloco em `_data/galleries.yml`:
   ```yaml
   - name: Nome do Álbum
     folder: nome-do-album
     photos:
       - file: foto1.jpg
         caption: ""
   ```

## Adicionar fotos a um álbum existente

1. Copie o arquivo para a pasta do álbum:
   ```
   cp foto.jpg images/nome-do-album/
   ```

2. Adicione uma entrada no bloco do álbum em `_data/galleries.yml`:
   ```yaml
       - file: foto.jpg
         caption: "Legenda opcional"
   ```

## Convenção de nomes

- Sem espaços → use hífens: `minha-foto.jpg`, não `minha foto.jpg`
- Sem acentos: `sao-paulo.jpg`, não `são-paulo.jpg`
- Tudo em minúsculas
- O nome da pasta em `folder:` deve ser idêntico ao nome da pasta em `images/`

## Testar localmente

```bash
bundle exec jekyll serve
```

Abra `http://localhost:4000/pictures.html` e verifique se o álbum aparece e as fotos carregam.

## Publicar

```bash
git add images/nome-do-album/ _data/galleries.yml
git commit -m "Add album: nome-do-album"
git push origin main
```

O site atualiza em ~1 minuto após o push.
