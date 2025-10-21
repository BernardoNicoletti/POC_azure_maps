# POC_azure_maps
Azure_maps

| **Empresa**                           | **AWS**                                                                                                             | **Microsoft Windows Azure**                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Serviço**                           | Amazon Location Service                                                                                             | Azure Maps                                                                                                    |
| **Pagamento**                         | Modelo “pay as you go” (pague pelo uso). Cobrança por chamadas de API (mapas, rotas, geocodificação, rastreamento). | Modelo “pay as you go”. Cobrança por transações de API (mapas, geocodificação, rotas, tráfego, etc).          |
| **Suporte**                           | Planos de suporte: Básico (gratuito), Developer, Business e Enterprise.                                             | Planos de suporte: Básico (gratuito), Developer, Standard e Professional Direct.                              |
| **Serviço de hospedagem de arquivos** | Amazon S3 — pode armazenar dados de localização, logs e arquivos de mapas customizados.                             | Azure Blob Storage — pode armazenar imagens de mapas, camadas personalizadas e dados geoespaciais.            |
| **Sistema operacional**               | Compatível com Windows, Linux e macOS.                                                                              | Compatível com Windows, Linux e macOS.                                                                        |
| **Linguagem de programação**          | SDKs e APIs REST para Python, Java, JavaScript, .NET, Go.                                                           | SDKs e APIs REST para .NET, Java, Python, JavaScript, Node.js, Android e iOS.                                 |
| **Banco de Dados**                    | Integra com Amazon RDS, DynamoDB e Redshift para análise e armazenamento de dados espaciais.                        | Integra com Azure SQL Database, Cosmos DB e PostgreSQL (com suporte a dados geoespaciais).                    |
| **Suporte ao serviço**                | Documentação oficial, exemplos práticos e integração com AWS CloudWatch, Cognito e IAM.                             | Documentação completa, Microsoft Learn, exemplos práticos e integração com Azure Active Directory e Power BI. |
| **Casos de uso**                      | Rastreamento de ativos, geofencing, logística, análise de localização, aplicações IoT e mobile.                     | Roteamento, análise de tráfego, visualização de dados espaciais, geocodificação e aplicativos logísticos.     |
| **Fornecedores de mapas**             | Esri e HERE (dados e renderização de mapas).                                                                        | TomTom e OpenStreetMap (dados e renderização de mapas).                                                       |
| **Nível de complexidade**             | Médio — requer configuração de permissões IAM e integração via SDK ou API.                                          | Médio — requer chave de autenticação e integração via API REST ou SDK.                                        |

🧭 POC — Azure Maps com Autocomplete e Geolocalização
🎯 Objetivo

O objetivo deste POC é demonstrar o uso do Microsoft Azure Maps, um serviço de geolocalização da plataforma Azure, integrando um mapa interativo com recursos de busca de endereços (autocomplete) e detecção da localização atual do usuário via navegador.

🧩 Tecnologias utilizadas

HTML5 e CSS3 – para estrutura e estilo da página;

JavaScript (ES6) – para integração com as APIs REST do Azure Maps;

Azure Maps SDK for Web (v3) – para renderização do mapa e autenticação via chave;

API Search Address – para sugestões de endereços (autocomplete);

API de Geolocalização do navegador – para detectar a posição atual do usuário.

🪜 Passos do Desenvolvimento (Tutorial)
1. Criação da conta no Azure

Acesse o portal: https://portal.azure.com

Crie uma conta gratuita (ou use uma existente).

No painel principal, pesquise por “Azure Maps Accounts”.

Clique em “+ Criar” e configure:

Nome do recurso (ex: poc-azure-maps);

Grupo de recursos (pode ser um novo);

Região (ex: Brazil South);

Plano de preço: S0 (padrão) ou gratuito.

Após criar, vá até o recurso e copie a Subscription Key (chave primária).

2. Montagem do ambiente

Crie um arquivo chamado index.html e insira o código abaixo:

<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>POC - Azure Maps com Autocomplete</title>
  <link rel="stylesheet" href="https://atlas.microsoft.com/sdk/javascript/mapcontrol/3/atlas.min.css">
  <script src="https://atlas.microsoft.com/sdk/javascript/mapcontrol/3/atlas.min.js"></script>
</head>
<body>
  <!-- Código completo POC -->
</body>
</html>


🔑 Substitua o texto:

const subscriptionKey = "SUA_AZURE_MAPS_SUBSCRIPTION_KEY_AQUI";


pela chave real obtida no Azure.

3. Estrutura e funcionamento do POC

O mapa é inicializado centralizado em São Paulo (−23.5505, −46.6333).

Um campo de texto permite digitar endereços — conforme o usuário digita, são feitas chamadas à API de busca de endereços (search/address/json) retornando sugestões automáticas.

Ao clicar em uma sugestão, o mapa é reposicionado para o endereço escolhido e exibe um marcador no local.

O botão “📍 Pegar minha localização” utiliza a API de geolocalização do navegador para identificar a posição atual do usuário e exibi-la no mapa.

4. Execução

Salve o arquivo como index.html.

Abra o arquivo em um navegador moderno (Edge, Chrome ou Firefox).

Permita o acesso à localização, caso solicitado.

Teste digitando endereços no campo de busca (ex: “Avenida Paulista”).

5. Resultados esperados

O mapa é carregado corretamente.

Ao digitar um endereço, aparecem sugestões automáticas.

Ao selecionar uma sugestão, o mapa foca na localização e exibe um marcador.

Ao clicar em “📍 Pegar minha localização”, o mapa centraliza na posição atual do usuário.

⚙️ Principais APIs utilizadas
| API                           | Descrição                                              | Endpoint                                                               |
| ----------------------------- | ------------------------------------------------------ | ---------------------------------------------------------------------- |
| **Search Address**            | Retorna endereços e locais com base em texto de busca. | `https://atlas.microsoft.com/search/address/json`                      |
| **Map Control SDK**           | Renderiza e controla o mapa interativo.                | `https://atlas.microsoft.com/sdk/javascript/mapcontrol/3/atlas.min.js` |
| **Geolocation API (Browser)** | Obtém a localização do usuário via GPS ou rede.        | `navigator.geolocation.getCurrentPosition()`                           |

🧩 Possíveis dificuldades encontradas
| **Dificuldade**                        | **Descrição / Solução**                                                                                                                 |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Autenticação falhou**                | Ocorre se a chave do Azure Maps não for configurada corretamente. Verifique se foi copiada da aba **“Authentication”** do portal Azure. |
| **Erro CORS (bloqueio de requisição)** | Pode acontecer ao abrir o arquivo diretamente. Solução: rodar um servidor local (ex: `npx http-server`).                                |
| **Mapas não aparecem**                 | Verifique se o navegador permite execução de JavaScript e se o link do SDK está acessível.                                              |
| **Geolocalização negada**              | O navegador precisa de permissão de acesso à localização. Habilitar em “Configurações → Privacidade → Localização”.                     |
| **Autocomplete lento**                 | Pode ocorrer por limitação da rede ou do tempo de debounce. O código já implementa 400ms de atraso para otimizar chamadas.              |

🧠 Conclusão
Este POC demonstrou de forma prática como integrar o Azure Maps em uma aplicação web, incluindo renderização de mapas, busca de endereços e geolocalização em tempo real.
A experiência mostra a facilidade de uso do serviço e sua aplicabilidade em sistemas logísticos, aplicativos de entrega, controle de frota ou qualquer projeto que envolva dados geográficos.
