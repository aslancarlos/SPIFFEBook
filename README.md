# SPIFFEBook — Tradução pt-BR de *Solving the Bottom Turtle*

Tradução para **português brasileiro (pt-BR)** do livro ***Solving the Bottom
Turtle — a SPIFFE Way to Establish Trust in Your Infrastructure via Universal
Identity***, a principal obra de referência sobre **SPIFFE** e **SPIRE**.

> ⚠️ **Projeto de tradução não oficial.** Esta é uma obra derivada, traduzida
> de forma independente. Não é endossada nem revisada pelos autores originais,
> pela SPIFFE/SPIRE, pela CNCF ou pela HPE.

## 📖 Ler online

A tradução está publicada para **leitura online**, capítulo a capítulo, via
**ReadTheDocs**:

**➡️ <https://spiffebook.readthedocs.io/>**

Capítulos:

1. [História e Motivação para o SPIFFE](docs/livro/01-historia-e-motivacao.md)
2. [Benefícios](docs/livro/02-beneficios.md)
3. [Conceitos Gerais de Identidade](docs/livro/03-conceitos-de-identidade.md)
4. [Introdução aos Conceitos SPIFFE e SPIRE](docs/livro/04-introducao-spiffe-spire.md)
5. [Antes de Começar](docs/livro/05-antes-de-comecar.md)
6. [Projetando uma Implantação SPIRE](docs/livro/06-projetando-implantacao-spire.md)
7. [Integrando com Outros](docs/livro/07-integrando-com-outros.md)
8. [Usando Identidades SPIFFE para Informar a Autorização](docs/livro/08-informar-autorizacao.md)
9. [Comparando SPIFFE com Outras Tecnologias](docs/livro/09-comparando-tecnologias.md)
10. [Histórias de Profissionais](docs/livro/10-historias-de-profissionais.md)

Complementos: [Notas de Tradução](docs/livro/notas-traducao.md) ·
[Sobre Zero, a Tartaruga](docs/livro/sobre-zero.md) ·
[Glossário do livro](docs/livro/glossario.md) · [Epílogo](docs/livro/epilogo.md)

## 📖 Sobre a obra

| | |
|---|---|
| **Obra original** | *Solving the Bottom Turtle* (2020), ISBN 978-0-578-77737-5 |
| **Autores originais** | Daniel Feldman, Emily Fox, Evan Gilman, Ian Haken, Frederick Kautz, Umair Khan, Max Lambrecht, Agustín Martínez Fayó, Eli Nesterov, Andrés Vega, Michael Wardrop, Brandon Lum |
| **Original em** | <https://spiffe.io/book/> |
| **Licença** | Creative Commons Attribution 4.0 International (CC BY 4.0) |
| **Idioma desta tradução** | Português (pt-BR) |
| **Tradução** | Aslan Carlos M. Ramos |
| **Status** | 🚧 Em andamento |

## 🛠️ Como é construído o site

A documentação é gerada com **[MkDocs](https://www.mkdocs.org/)** (tema
*Material*) a partir dos arquivos em [`docs/`](./docs) e publicada
automaticamente pelo ReadTheDocs (configuração em
[`.readthedocs.yml`](./.readthedocs.yml) e [`mkdocs.yml`](./mkdocs.yml)).

Para visualizar localmente:

```bash
pip install -r docs_requirements.txt
mkdocs serve
# abra http://127.0.0.1:8000
```

> A fonte editável original (texto/diagramação) **não é distribuída** neste
> repositório; o conteúdo publicado é o de [`docs/`](./docs).

## ⚖️ Licença e atribuição

Tanto a obra original quanto esta tradução estão sob **[CC BY 4.0](./LICENSE)**.
Você pode compartilhar e adaptar, inclusive comercialmente, **desde que dê o
crédito apropriado** e **indique se fez alterações**.

Os detalhes de atribuição e a declaração de modificações (esta é uma tradução)
estão em **[NOTICE.md](./NOTICE.md)** — leitura obrigatória ao reutilizar.

## 🤝 Contribuindo

Correções de tradução, revisão e padronização de terminologia são bem-vindas.
Veja **[CONTRIBUTING.md](./CONTRIBUTING.md)** e o **[GLOSSARIO.md](./GLOSSARIO.md)**
(terminologia EN → pt-BR para manter consistência).

## 📚 Recursos sobre SPIFFE/SPIRE

- Site oficial: <https://spiffe.io>
- SPIFFE no GitHub: <https://github.com/spiffe>
- CNCF (SPIFFE/SPIRE são projetos graduados): <https://www.cncf.io>
