# Capítulo 10 — Histórias de Profissionais

<p><em>Histórias reais de organizações que adotaram SPIFFE e SPIRE em produção.</em></p>
<h2 id="section-1"></h2>

Este capítulo inclui cinco histórias de praticantes, engenheiros de empresas reais que implementaram SPIFFE e SPIRE.

## Uber: Protegendo Infraestrutura de Próxima Geração e Legada com Identidade Criptográfica

Ryan Turner, Software Engineer 2, Uber

Na última década, a Uber se tornou o principal exemplo de crescimento explosivo. Conforme o número de serviços de software e a escala geográfica em que operamos cresceram, a complexidade e o risco também aumentaram. Para atender às necessidades crescentes, começamos a construir nossa plataforma de infraestrutura de próxima geração. Simultaneamente, alguns anos atrás, vimos alguma tração inicial nos projetos de código aberto SPIFFE e SPIRE.

Imediatamente vimos o valor que SPIFFE poderia trazer ao nos permitir fortalecer a postura de segurança de nossa infraestrutura de próxima geração. Implementamos SPIRE na Uber e agora estamos usando-a para estabelecer confiança em vários ambientes de carga de trabalho usando identidades criptograficamente verificáveis. Começamos com alguns serviços de aplicação e internos, como um mecanismo de fluxo de trabalho que roteia múltiplas cargas de trabalho dinâmicas para completar tarefas específicas, acessando dados em toda a plataforma. SPIRE fornece identidades SPIFFE para nossas cargas de trabalho ao longo de todo o nosso ciclo de aplicação. SPIFFE é usada para autenticar serviços e nos ajuda a evitar configurações incorretas que podem resultar em problemas em produção.

## Adaptando SPIRE à Pilha Legada

SPIRE agora é um componente-chave da infraestrutura de próxima geração da Uber, mas também estamos usando uma abordagem de sidecar para adaptar autenticação à infraestrutura legada. Embora SPIFFE e SPIRE sejam conhecidas por funcionar em arquiteturas cloud native modernas, podemos adaptar os projetos à nossa pilha legada proprietária rapidamente. SPIRE pode fornecer uma ponte crítica de confiança dentro da infraestrutura de próxima geração e legada da Uber e impactar positivamente a segurança interna e a eficiência do desenvolvedor.

Durante nossa jornada, a comunidade SPIFFE foi muito supportiva em nos ajudar a encontrar soluções. Como resultado, nossos engenheiros têm contribuído ativamente com código aos projetos também.

## Equipes de Segurança, Desenvolvimento e Auditoria Estão se Beneficiando do SPIFFE

SPIFFE dá à nossa equipe de segurança mais confiança na infraestrutura de backend e menos dependência de controles de segurança baseados em rede. Conforme lidamos com dados financeiros e operamos através de limites geográficos, precisamos controlar o acesso a dados financeiros e de clientes. Com SPIRE, podemos fornecer uma identidade fortemente atestada para controle de acesso. Nos ajuda a atender esses requisitos e reduz o ônus das equipes de auditoria no processo.

Nossas equipes de desenvolvimento na Uber usam bibliotecas de cliente consistentes para criar políticas de AuthZ usando identidades baseadas em SPIFFE. Os projetos permitiram que equipes de desenvolvimento aproveitassem primitivos de identidade de carga de trabalho, como X.509 e JWT, sem precisar de uma compreensão profunda de tópicos complexos, como inicialização de confiança, introdução segura, provisionamento de credenciais ou rotação.

## Pinterest: Superando a Crise de Identidade com SPIFFE

Jeremy Krach, Senior Security Engineer, Pinterest

Em 2015, o Pinterest estava passando por uma crise de identidade. A infraestrutura da empresa estava crescendo em direções diversas e divergentes. Cada novo sistema resolveu a autenticação - o problema de identidade - de sua forma única. Desenvolvedores gastavam horas a cada mês em reuniões e revisões de segurança para projetar, modelar ameaças e implementar suas soluções de identidade customizadas ou integrar seu novo serviço a modelos de identidade díspares de suas dependências. Ficou claro que a equipe de segurança precisava construir uma infraestrutura comum para fornecer identidade de forma genérica que pudesse ser usada em nossos serviços heterogêneos.

O rascunho inicial deste sistema atribuiu identidade às máquinas por meio de certificados X.509 baseados em nomes de host. Era muito usado para gerenciamento de segredos, mas adoção mais ampla ainda não havia ocorrido. Conforme continuamos a escalar, particularmente com sistemas multi-tenant como o Kubernetes, precisávamos de identidades mais refinadas, não ligadas a hosts específicos em nossa infraestrutura, mas sim à identidade do próprio serviço.

Entra SPIFFE.

## Simplificando Complexidades com SPIFFE

SPIFFE agora fornece identidade uniforme na maior parte de nossa infraestrutura. Inicialmente, começamos com Kubernetes, pois a necessidade era mais clara nesse ambiente multi-tenant. Depois, movemos o restante da infraestrutura para SPIFFE como sua identidade principal. Como resultado, quase todo serviço no Pinterest tem um nome padronizado que podemos usar, e não há convenções obscuras nem esquemas desconexos. Nos ajudou a unificar e padronizar nossas convenções de identidade, que se alinharam às de outros projetos internos para identificar atributos de serviço, como a propriedade de serviço.

Aproveitamos SPIFFE como a identidade em ACLs para gerenciamento de segredos, comunicação mTLS de serviço a serviço e até mesmo políticas de autorização genéricas. Knox, serviço de gerenciamento de segredos de código aberto do Pinterest, usa certificados de identidade SPIFFE X.509 como um método de autenticação suportado.

## Dev, Sec e Ops estão em harmonia novamente

SPIFFE torna mais fácil para a equipe de segurança escrever políticas de autorização. A velocidade dos desenvolvedores é significativamente maior, pois nossos engenheiros não precisam se preocupar com esquemas customizados ou integrações díspares de autenticação. Como agora temos uma forma padrão de interpretar identidade em toda nossa infraestrutura, é muito mais fácil para as equipes de faturamento e propriedade determinar quem é o proprietário de um serviço. Ter um forte senso de identidade também é conveniente para a consistência do logging e do rastreamento. Estamos entusiasmados com o futuro do projeto SPIFFE e gratos por sua capacidade de nos ajudar a resolver nossa crise de identidade!

## ByteDance: Fornecendo Autenticação de Discagem para Serviços em Escala Web

Eli Nesterov, Security Engineering Manager, ByteDance

ByteDance, a empresa por trás do TikTok, construiu e implantou serviços de internet em larga escala em todo o mundo que servem milhões de usuários. Sua infraestrutura apoiando esses serviços é uma mistura de data centers privados e provedores de nuvem pública. Suas aplicações executam em múltiplos clusters Kubernetes e nós dedicados em plataformas na forma de milhares de microsserviços.

Conforme crescemos em escala e tamanho, tínhamos múltiplos mecanismos de autenticação em nossas plataformas usando tudo, desde PKI's, tokens JWT, Kerberos, OAuth e estruturas customizadas. Adicione inúmeras linguagens de programação a esses mecanismos de autenticação, e a complexidade operacional e o risco aumentaram ainda mais. Operacionalmente tornou-se complexo para nossa equipe de segurança e operações gerenciar esses esquemas de autenticação. No caso de uma vulnerabilidade conhecida em um framework de autenticação, não poderíamos nos mover rapidamente, pois cada framework tinha que ser tratado separadamente. Em alguns casos, eles tinham dependências em nível de código, o que tornava ainda mais difícil mudar. Auditoria e conformidade através de limites geográficos eram desafiadoras, pois cada abordagem de autenticação específica de plataforma teve que ser revisada e governada separadamente.

Uma mudança em direção à arquitetura baseada em zero trust em geral, e um esforço para melhorar nossa produtividade do desenvolvedor, nos forçou a construir um plano de gerenciamento de identidade unificado para nossos serviços que escalonaria para nossas necessidades crescentes.

## Construindo PKI em Escala Web com SPIRE

É difícil construir um sistema de identidade que funcione através de diferentes ilhas de infraestrutura ou plataformas como a nossa. Poderíamos ter criado o nosso próprio, mas teria requerido uma quantidade significativa de esforço. Seguimos adiante com SPIRE, pois forneceu a escala e flexibilidade no suporte a uma ampla variedade de plataformas que precisávamos e em escala web. Como oferece identidade criptográfica baseada em certificados X.509 padrão, nos ajuda a facilmente habilitar mTLS, que por padrão atende a muitos dos requisitos de conformidade. Extensibilidade e ser código aberto foram outro plus, pois poderíamos facilmente integrá-lo com nossas pilhas de plano de controle e dados existentes.

## Autenticação Transparente Simplificou Operações

Com SPIRE podemos implantar uma autenticação consistente de 'discagem' em todas nossas plataformas. O fardo da autenticação e segurança agora está encapsulado dos desenvolvedores para que possam focar em lógica de negócios ou aplicação. Isso melhorou nossa velocidade geral de implantação. Também temos menos probabilidade de obter 'erros de produção' devido a problemas de configuração, como usar credenciais de desenvolvimento em produção. Autenticação padronizada com SPIRE também simplificou conformidade e auditoria, já que temos mTLS através de domínios de confiança e plataformas. SPIRE também nos permitiu mover para um modelo mais semi-descentralizado em termos de distribuição de identidade, onde o sistema de identidade é local para, digamos, um data center. Isso melhora nossa disponibilidade geral e nos posiciona bem para recuperação.

Somos praticamente 'à prova de futuro' com SPIRE, pois pode escalar e se adaptar para atender nossas necessidades crescentes de negócios.

## Anthem: Protegendo Aplicações Healthcare Cloud Native com SPIFFE

Bobby Samuel, VP AI Engineering, Anthem

Os custos crescentes de healthcare na indústria estão compelindo organizações como Anthem a inovar rapidamente e repensar como interagimos com provedores, grupos de empregadores e indivíduos. Como parte desta iniciativa, estamos desenvolvendo uma série de aplicações que nos ajudarão a reduzir custos abrindo seguramente acesso a dados de healthcare. Começamos a construir a infraestrutura de próxima geração de suporte baseada em tecnologias cloud native como Kubernetes. Esta nova infraestrutura impulsionará inovação rápida e engajará um ecossistema mais amplo de organizações e desenvolvedores. Um exemplo disso seria nossa plataforma HealthOS, que permitirá que terceiros construam capacidades para entregar em interfaces front-end, aproveitando um oceano de dados de saúde desidentificados.

Mas em quase toda grande empresa, especialmente organizações de healthcare, alguém está tentando obter seus dados com intenção maliciosa. Informação de Healthcare Protegida é vendida por muito mais do que informação financeira; assim, atores maliciosos como hackers encontram sistemas de healthcare altamente lucrativos. Com a adoção de arquiteturas cloud native, o risco e a complexidade aumentam ainda mais. O risco de uma violação é ainda maior, pois o raio de ameaça aumenta significativamente enquanto revisões de segurança manuais e processos se tornam inibidores em escala de nuvem.

## Construindo uma Fundação para Arquitetura Zero Trust

Não poderíamos confiar em ferramentas de segurança baseadas em parâmetros tradicionais e processos para proteger nossas aplicações e infraestrutura de próxima geração. Zero trust, uma abordagem de segurança automatizada e refinada, fazia muito sentido para nós, especialmente no futuro, pois planejamos operar através de limites organizacionais e provedores de nuvem. Identidade e autenticação tanto para usuários quanto para serviços estão entre os princípios centrais do modelo de segurança zero trust. Zero trust nos permite confiar menos em controles baseados em rede do que na autenticação de cada sistema ou carga de trabalho. SPIFFE e SPIRE habilitaram uma camada de autenticação fundamental para nossa arquitetura de segurança zero trust. Eles permitem que cada carga de trabalho prove criptograficamente 'quem eles são' antes de começar a se comunicar.

## Uma Mudança Afastada de Gerenciamento de Segredos

Tipicamente quando você pensa em autenticação, você pensa em nomes de usuário, senhas e bearer tokens. Infelizmente, esses tipos de credenciais estavam se tornando um risco e fonte de complexidade na Anthem. Tendem a ser de longa vida, e o gerenciamento ou rotação destes era complicado. Queríamos nos afastar desse tipo de práticas de gerenciamento de segredos em geral. Em vez de perguntar a um serviço 'o que você tem,' queremos perguntar 'quem você é.' Em suma, queríamos nos mover para identidades criptográficas como SPIFFE. Podemos ver benefícios adicionais do uso de uma identidade fortemente atestada no futuro, como estabelecer mTLS entre cargas de trabalho e elevar a identidade até as aplicações.

## Construindo Segurança como Parte da Infraestrutura com SPIFFE

Segurança é frequentemente considerada um inibidor para implantação pelas equipes de desenvolvimento. As equipes DevOps querem implantar novos recursos inovadores mais rapidamente. No entanto, eles têm que passar por tickets manuais, processos, integrações e revisões relacionadas aos controles de segurança. Na Anthem, dobramos nossa estratégia removendo obstáculos para nossas equipes de desenvolvimento fazendo segurança uma função da infraestrutura. Com a adoção de tecnologias como SPIFFE, podemos abstrair a complexidade dos controles de segurança das equipes de desenvolvimento e fornecer regras consistentes em várias plataformas. SPIFFE, juntamente com outras tecnologias baseadas em zero trust, nos ajudará a reduzir nosso tempo de provisão de sistema de três meses para menos de duas semanas na maioria dos cenários. Segurança está se tornando um facilitador na Anthem com SPIFFE liderando a carga.

## Square: Estendendo Confiança para a Nuvem

Michael Weissbacher e Mat Byczkowski, Senior Security Engineers, Square

Square fornece uma ampla variedade de serviços financeiros. Durante sua vida, a empresa cresceu novas unidades de negócios de dentro da empresa, como Capital e Cash, mas também adquiriu empresas como Weebly e Stitch Labs. Diferentes unidades de negócios usam diferentes tecnologias e podem operar a partir de diferentes data centers e nuvens enquanto ainda precisam se comunicar sem problemas.

Nosso sistema de identidade de serviço desenvolvido internamente precisava escalar além da arquitetura interna que Square desenvolveu para seus data centers. Queríamos expandir o sistema para a nuvem e queríamos fornecer um sistema igualmente seguro que também nos serviria bem pelos próximos anos. Idealmente estávamos procurando por uma ferramenta baseada em padrão aberto que também se integrasse perfeitamente com o proxy Envoy. Tanto SPIFFE quanto SPIRE apoiavam nossos objetivos de crescimento e plataformas independentes trabalhando com múltiplas nuvens e ferramentas de implantação.

## Um Padrão Aberto que Funciona com Projetos de Código Aberto Populares

Como SPIFFE era baseada em padrões abertos existentes como Certificados X.509, forneceu um caminho de upgrade claro de como fazíamos identidade de serviço. Envoy é o bloco de construção fundamental de como os apps se comunicam na Square. Como SPIRE suporta a API de Descoberta de Segredos do Envoy, obter X509-SVIDs foi fácil. Envoy tem controles de acesso integrados que podem usar identidades SPIFFE para decidir quais apps estão permitidas a se comunicar.

Implantamos a arquitetura SPIRE em paralelo com o sistema de identidade de serviço existente, então fizemos alterações em várias ferramentas internas e frameworks para suportar ambos os sistemas. Em seguida, integramos SPIRE com o sistema de implantação para registrar todos os serviços em SPIRE. Isto significava que poderíamos testar a carga do SPIRE com rotação frequente de SVID. Finalmente, usamos feature flags para lentamente optar-in serviços para começar a usar SVIDs em suas chamadas serviço-a-serviço.

## Conectividade Segura e sem Fricção Através de Nuvem e Data Centers

SPIFFE e SPIRE estão habilitando nossa equipe de Infraestrutura de Segurança a fornecer uma ponte crítica para conectar seguramente diferentes plataformas e tecnologias. Ainda estamos no estágio inicial de migração para SPIRE, mas as mudanças que colocamos em lugar nos permitiram conectar sem problemas nossa infraestrutura AWS EKS de produção com serviços implantados aos data centers da Square. Agora estamos trabalhando em uma federação automatizada entre nossos domínios de confiança, pois apenas federamos manualmente antes. Usamos identidade SPIFFE como um padrão, mesmo para o trabalho de identidade customizado que fazemos na empresa.

Também estamos realmente felizes em nos envolver com a comunidade SPIFFE, todos têm sido amigáveis e úteis durante nossa jornada. A comunidade forneceu um benefício adicionado de um bom lugar para discutir ideias de design de sistema para sistemas zero trust em geral.
