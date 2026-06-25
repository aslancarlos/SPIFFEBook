# Glossário de Tradução (EN → pt-BR)

Terminologia padronizada para manter **consistência** ao longo da tradução.
Quando um termo é amplamente conhecido em inglês na comunidade, mantemos o termo
original (eventualmente com explicação na primeira ocorrência).

> Convenção: a coluna **Tradução** mostra a forma preferida. "(manter EN)"
> indica que o termo em inglês deve ser preservado.

| Inglês | Tradução (pt-BR) | Notas |
|---|---|---|
| workload | carga de trabalho / *workload* | Preferir "*workload*" (itálico) quando se referir ao conceito SPIFFE; "carga de trabalho" em texto corrido. Manter consistente por capítulo. |
| trust domain | domínio de confiança | |
| attestation | atestação | |
| node attestation | atestação de nó | |
| workload attestation | atestação de *workload* | |
| identity | identidade | |
| universal identity | identidade universal | |
| issuer | emissor | |
| trust bundle | *trust bundle* (manter EN) | Explicar como "pacote/conjunto de confiança" na 1ª ocorrência. |
| SPIFFE ID | SPIFFE ID (manter EN) | Nome próprio do padrão. |
| SVID (SPIFFE Verifiable Identity Document) | SVID (manter EN) | Expandir na 1ª ocorrência. |
| X.509-SVID / JWT-SVID | X.509-SVID / JWT-SVID (manter EN) | |
| Workload API | *Workload API* (manter EN) | |
| turtles all the way down | "tartarugas até embaixo" | Referência do título; manter a metáfora e explicar. |
| bottom turtle | "tartaruga de baixo" | |
| bootstrapping | *bootstrapping* (manter EN) | "inicialização de confiança" como apoio. |
| secret zero / bottom turtle problem | problema do *secret zero* | |
| trust | confiança | |
| chain of trust | cadeia de confiança | |
| mutual TLS (mTLS) | TLS mútuo (mTLS) | |
| federation | federação | |
| registration entry | entrada de registro | |
| selector | seletor | |
| agent / server (SPIRE) | agente / servidor (SPIRE) | Nomes de componentes do SPIRE. |

## Regras de estilo

- **Nomes próprios de projetos e padrões** (SPIFFE, SPIRE, SVID, SPIFFE ID,
  Workload API) **não são traduzidos**.
- **Siglas**: expandir na primeira ocorrência, depois usar a sigla.
- **Código, comandos e nomes de arquivos**: nunca traduzir.
- **Citações de RFCs/specs**: manter o título original em inglês.
- Preferir **português claro** a traduções literais que soem artificiais.
