# Capítulo 9 — Comparando SPIFFE com Outras Tecnologias de Segurança

*Os problemas que SPIFFE e SPIRE resolvem não são novos — todo sistema distribuído precisa de alguma forma de identidade para ser seguro. No entanto, as formas existentes de identidade não são adequadas para identificar serviços internos dentro de uma organização. SPIFFE e SPIRE são atualmente a única solução completa para o problema de identidade de serviços.*

|  |  |  |  |
|----|----|----|----|
| **Tecnologia** | **O que oferece** | **Limitações para serviços internos** | **Como SPIFFE/SPIRE complementa ou supera** |
| Web PKI | Emissão e renovação automáticas via Domain Validation (DV). | Requer DNS individual por serviço; qualquer serviço local pode obter certificado via token HTTP; inadequado para serviços internos sem DNS. | SPIRE usa attestation baseada em kernel/plataforma — sem dependência de DNS ou tokens HTTP interceptáveis. |
| Active Directory + Kerberos | Ticket-based; TGS centralizado; suporte a machine accounts. | Requer chamada ao TGS para cada recurso acessado; acoplamento forte a hostnames; rotação de chaves exige coordenação manual. | SVIDs são validados localmente no trust domain — sem roundtrip por recurso. Rotação automática sem coordenação entre serviços. |
| OAuth 2.0 / OIDC | Delegação de acesso com tokens; suporte a service accounts. | Workload precisa de uma credencial pré-existente (client secret, refresh token) para obter o token — perpetua o problema do 'secret zero'. | SPIRE emite SVIDs sem nenhuma credencial prévia; SVIDs podem atuar como tokens OAuth, complementando o ecossistema. |
| Secret Managers (Vault, etc.) | Armazenamento seguro, auditoria e rotação de segredos. | O workload ainda precisa de uma credencial para autenticar ao secret manager — 'credential zero' não resolvido. | SPIFFE resolve a autenticação ao secret manager (ex: Vault TLS Cert Auth), eliminando o credential zero. |
| Service Meshes (Istio, Consul) | Proxy automático, mTLS, autorização e observabilidade. | Identidade frequentemente acoplada a primitivos específicos (ex: Kubernetes); sem suporte a serviços off-mesh. | SPIRE provê identidade universal — on-mesh e off-mesh. Meshes podem usar SPIRE como identity provider para interoperabilidade. |
| Overlay Networks | Rede virtual unificada entre plataformas via encapsulamento IP. | Não atestam identidade dos serviços antes de permitir conexão; dependem de certificado pré-existente. | SPIFFE é complementar: fornece certificados atestados para nós de overlay networks. |

## Web PKI

O Web PKI funciona muito bem para sites seguros na internet, mas não é adequado para identidade de serviços internos: muitos serviços internos não têm nomes DNS individuais; o processo de validação de certificados via Domain Validation (DV) pode ser comprometido por qualquer serviço que consiga responder ao token HTTP; e qualquer serviço na rede local pode obter um certificado.

## Active Directory (AD) e Kerberos

O Kerberos requer uma chamada ao Ticket Granting Service (TGS) para cada recurso acessado — o que resulta em protocolos mais verbosos e reduz a confiabilidade. A rotação de material de chave exige coordenação entre o serviço e o TGS, e o protocolo acopla serviços a hostnames. O SPIRE supera essas limitações: SVIDs são validados localmente no trust domain;, sem roundtrip por recurso, a rotação é automática e sem coordenação; e múltiplos SVIDs por workload são suportados nativamente.

## OAuth e OpenID Connect (OIDC)

OAuth foi projetado para pessoas e delegação de acesso, não para entidades não-humanas. Para que um workload obtenha um token OAuth, ele precisa de uma credencial pré-existente (client secret, senha ou refresh token) — o que não resolve o problema da 'tartaruga do fundo'. O SPIRE permite que SVIDs sejam usados para autenticar junto ao provedor OAuth, eliminando a necessidade de gerenciar credenciais OAuth diretamente. SVIDs podem complementar o ecossistema OAuth, mas não substituí-lo.

## Secret Managers

Secret managers melhoram significativamente a postura de segurança de sistemas que dependem de segredos compartilhados, mas perpetuam o uso de segredos compartilhados. O desafio central — como o workload autentica-se com o Secret Manager — não é resolvido pelo Secret Manager. O SPIFFE resolve exatamente esse problema: usando SVIDs para autenticar no secret manager (como o Vault TLS Cert Auth), elimina o 'credential zero'.

## Service Meshes

A maioria das implementações de service mesh inclui mecanismos de autenticação de serviço nativos da plataforma — e muitas implementam partes da especificação SPIFFE (como Istio e Consul). Porém, soluções como o Istio acoplam a identidade a primitivos específicos do Kubernetes, sem suporte a serviços fora do mesh. O SPIRE fornece um plano de controle de identidade universal — tanto dentro quanto fora do mesh. Service meshes são complementares ao SPIFFE/SPIRE, não alternativas.

## Overlay Networks

Redes overlay simulam uma rede unificada para serviços em múltiplas plataformas, usando conceitos de rede padrão, como endereços IP e tabelas de roteamento. As implementações mais recentes têm recursos de autenticação, mas geralmente não atestam a identidade dos serviços antes de permitir conexões — dependendo de um certificado pré-existente. O SPIFFE é complementar, fornecendo certificados atestados para nós de overlay networks.

<table style="width:99%;">
