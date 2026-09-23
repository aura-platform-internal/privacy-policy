# Site da Política de Privacidade do Aura

**Data:** 23 de setembro de 2026  
**Status:** aprovado para planejamento

## Objetivo

Criar uma página pública, clara e responsiva que explique como a Filmaro Corp trata dados pessoais na plataforma Aura. A página será a URL oficial de privacidade usada no site, no fluxo de autenticação da Meta e nos demais pontos em que o usuário precise consultar essas informações.

## Publicação

O código ficará no repositório público `aura-platform-internal/privacy-policy` e será publicado pelo GitHub Pages. A configuração inicial poderá usar a URL fornecida pelo GitHub Pages. A forma recomendada para produção é associar posteriormente um endereço próprio e estável, como `privacidade.aura-platform.filmaro.com.br`.

O site principal do Aura e as configurações da aplicação na Meta devem apontar para essa URL. O endereço da política deve permanecer estável mesmo que o frontend principal seja substituído ou implantado em outro provedor.

## Identidade e contato

- **Controladora:** Filmaro Corp
- **Canal de privacidade:** wudarski@filmaro.com.br
- **Idioma inicial:** português do Brasil
- **Legislação de referência:** Lei Geral de Proteção de Dados Pessoais (LGPD)

O canal de privacidade será apresentado como o meio para exercer direitos, pedir informações, corrigir dados, revogar consentimento e solicitar exclusão.

## Escopo dos dados descritos

A política refletirá os fluxos que existem nos projetos `aura-api-go` e `aura-front`:

1. **Dados da conta do Instagram/Meta:** identificador da conta, nome de usuário, nome e foto do perfil, token de acesso e permissões autorizadas pelo usuário.
2. **Conteúdo do Instagram selecionado para uso no Aura:** publicações, links, imagens, datas, comentários, nomes públicos dos autores dos comentários, curtidas e métricas disponíveis pela API.
3. **Resultados de análise:** classificação de sentimento, agrupamentos, pontuação, comentários destacados, estado e data da análise.
4. **Conta Aura:** identificador interno, permissões, e-mail informado, estado de verificação do e-mail e dados técnicos de autenticação. Tokens e códigos sensíveis serão descritos pelo propósito, sem expor detalhes que enfraqueçam a segurança.
5. **Assinaturas:** plano, situação da assinatura, identificadores do provedor e informações necessárias para criar, acompanhar ou cancelar uma assinatura. A política esclarecerá que os dados completos do cartão são tratados pelo provedor de pagamento e não são recebidos pelo Aura.
6. **Dados técnicos:** registros necessários para segurança, diagnóstico, prevenção de fraude e operação do serviço, limitados ao que efetivamente for gerado pela infraestrutura e pela aplicação.

## Finalidades e bases legais

A página relacionará cada grupo de dados às finalidades correspondentes: autenticar o usuário, integrar o Instagram, listar conteúdo autorizado, produzir análises de sentimento, manter a sessão, verificar e-mail, administrar planos e assinaturas, prestar suporte, proteger o serviço e cumprir obrigações legais.

As bases legais serão apresentadas de modo contextual, incluindo execução do serviço solicitado pelo usuário, consentimento quando aplicável à autorização da integração, legítimo interesse para segurança e melhoria operacional e cumprimento de obrigação legal ou regulatória. A redação evitará afirmar que todo tratamento depende exclusivamente de consentimento.

## Inteligência artificial

A política informará de forma destacada que comentários associados às publicações selecionadas são enviados ao provedor de IA para classificação de sentimento. Explicará que o resultado é automatizado, pode conter imprecisões e serve como apoio analítico.

O Aura não usará essa análise para tomar decisões jurídicas, financeiras, de crédito, emprego ou outras decisões de efeito semelhante sobre o usuário ou os autores dos comentários.

## Compartilhamento e operadores

Serão identificadas as categorias e finalidades dos fornecedores envolvidos:

- **Meta/Instagram:** autenticação e acesso ao conteúdo autorizado;
- **Groq:** processamento dos comentários para análise por IA;
- **Mercado Pago:** criação e gestão de assinaturas e pagamentos;
- **Resend:** envio de mensagens de verificação e comunicações transacionais;
- **Locaweb:** infraestrutura de hospedagem da aplicação e do banco de dados;
- **GitHub Pages:** hospedagem desta página pública.

A política explicará que alguns fornecedores podem tratar dados fora do Brasil conforme suas próprias infraestruturas e contratos. Não incluirá o Doppler como destinatário de dados pessoais, pois seu uso atual é restrito a segredos e configurações da aplicação.

## Armazenamento, retenção e segurança

A redação não prometerá prazos que o produto ainda não implementa. Informará que os dados são mantidos pelo período necessário para fornecer o serviço, proteger a plataforma, resolver disputas e cumprir obrigações legais. Após o término da finalidade ou uma solicitação válida, os dados serão eliminados ou anonimizados, ressalvadas as hipóteses legais de conservação.

As medidas de segurança serão descritas por categorias, como controle de acesso, proteção de credenciais, restrição de privilégios e monitoramento operacional. A página não divulgará segredos, topologia detalhada ou garantias absolutas de segurança.

## Direitos e exclusão de dados

A política descreverá os direitos previstos na LGPD: confirmação, acesso, correção, informação sobre compartilhamento, portabilidade quando aplicável, anonimização, bloqueio, eliminação, oposição, revogação do consentimento e revisão ou explicação sobre tratamento automatizado.

Uma seção com o identificador `exclusao-de-dados` fornecerá instruções objetivas para:

1. enviar a solicitação ao endereço wudarski@filmaro.com.br;
2. informar os dados suficientes para localizar a conta, sem enviar senhas ou tokens;
3. revogar o acesso do Aura nas configurações da Meta/Instagram;
4. entender que certos registros podem ser conservados quando houver obrigação legal ou necessidade legítima devidamente justificada.

Essa seção poderá ser usada como URL pública de instruções de exclusão no painel da Meta por meio do fragmento `#exclusao-de-dados`.

## Estrutura da página

A página terá:

- cabeçalho com marca Aura, título, data de vigência e resumo em linguagem simples;
- índice navegável;
- seções semânticas para dados coletados, uso, IA, compartilhamento, retenção, segurança, direitos, exclusão, menores, alterações e contato;
- cartões ou tabelas simples para tornar categorias de dados e fornecedores fáceis de localizar;
- rodapé com controladora, contato e link de retorno ao Aura.

## Implementação visual e técnica

O artefato principal será um único `index.html`, com CSS incorporado e sem JavaScript obrigatório. Ele não carregará fontes, bibliotecas, pixels, analytics ou recursos de terceiros. Isso reduz dependências, evita coleta adicional na própria página e permite publicação direta no GitHub Pages.

O layout seguirá uma estética moderna e sóbria, com alto contraste, largura de leitura confortável, tipografia baseada em fontes do sistema, navegação fixa apenas quando houver espaço e adaptação completa para telas pequenas. A página respeitará preferências de redução de movimento e terá foco visível para navegação por teclado.

O repositório também conterá:

- `README.md` com publicação pelo GitHub Pages e configuração de domínio próprio;
- arquivo `.nojekyll` para servir o conteúdo estático diretamente;
- `404.html` reutilizando ou redirecionando de forma simples para a política, caso seja útil para o endereço publicado;
- `CNAME` somente quando o domínio próprio estiver definido e o DNS estiver pronto.

## Validação

Antes da publicação, serão verificados:

- validade estrutural do HTML;
- leitura e navegação em larguras de celular e desktop;
- ausência de requisições externas desnecessárias;
- funcionamento do índice e do fragmento `#exclusao-de-dados`;
- presença da identificação da controladora e do canal de contato;
- correspondência entre a política e os dados e fornecedores observados no código atual dos projetos Aura;
- ausência de promessas técnicas ou jurídicas que o produto não consiga cumprir.

## Limites

O conteúdo será uma política operacional baseada no funcionamento atual do produto e nas exigências gerais de transparência da LGPD. Mudanças em fornecedores, dados coletados, finalidades, retenção ou funcionalidades exigirão revisão da página. Uma revisão jurídica profissional continua recomendável antes de usar o texto como documento contratual definitivo.
