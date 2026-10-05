# casanest-mcp — instruções para agentes

## Review guidelines

Aponta só problemas reais e graves (P0/P1): documentação que promete o que o servidor não faz,
dados privados ou segredos expostos e links que levam ao sítio errado. Não comentes estilo, nomes
ou gosto. Escreve as revisões em português de Portugal (o README é em inglês e assim fica).

Este repositório é só a documentação pública do servidor MCP do CasaNest
(`https://casanest.eu/mcp`). O código vive no repo `casanest`; a documentação técnica ao vivo
(`https://casanest.eu/casanest-ai.md`, server card, OpenAPI) é a autoridade.

### A documentação tem de ser verdadeira

- URL, transporte, autenticação («None») e nomes e propósito das ferramentas (`search_properties`,
  `get_property`, `compare_properties`, `get_area_statistics`) coincidem com a server card e o
  OpenAPI publicados. Uma ferramenta, parâmetro ou capacidade que não exista é P1.
- O âmbito é só leitura de anúncios públicos e de estatísticas do INE. Afirmar que publica, envia
  mensagens, reserva, paga ou mostra dados de conta ou CRM é P1. Estatísticas do INE não são preços
  pedidos, avaliações nem previsões.
- Presença em registos e diretórios (MCP Registry `eu.casanest/catalogue`, Glama) só com link
  verificável; não se inventam certificações, aprovações nem parcerias.

### Privacidade e segurança

- Exemplos e prompts não incluem dados pessoais nem pedem ao utilizador que os envie.
- Nenhuma chave, token, rota privada ou endpoint interno (backoffice, admin, CRM) no README; os
  exemplos `curl` usam só a API pública de leitura.
- Não se ensina a contornar limites de pedidos, pedidos recusados ou rotas privadas.
