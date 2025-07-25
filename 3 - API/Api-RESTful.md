# API RESTful

## 1. O que é REST?

REST (Representational State Transfer) é um estilo arquitetural descrito por Roy Fielding em sua tese de 2000 :contentReference[oaicite:1]{index=1}. APIs que seguem os princípios do REST são chamadas de **RESTful APIs** ou **REST APIs** :contentReference[oaicite:2]{index=2}.

## 2. Recursos (Resources)

- **Resource** é qualquer entidade com endereço único (URI), como usuário, documento ou coleção de itens :contentReference[oaicite:3]{index=3}.
- A **representação** do recurso (em JSON, XML, HTML etc.) contém dados, metadados e links HATEOAS que permitem a navegação entre estados :contentReference[oaicite:4]{index=4}.

## 3. Princípios Arquiteturais (Restrições REST)

1. **Interface Uniforme**: URLs consistentes, uso consistente de métodos HTTP e formatos padronizados de troca :contentReference[oaicite:5]{index=5}.
2. **Cliente-Servidor**: Separação de responsabilidades entre cliente e servidor para maior escalabilidade :contentReference[oaicite:6]{index=6}.
3. **Sem Estado (Statelessness)**: Cada requisição deve conter todas as informações necessárias, sem dependência de estado de sessão no servidor :contentReference[oaicite:7]{index=7}.
4. **Cacheável**: Respostas podem ser armazenadas conforme configuração, melhorando a eficiência e desempenho :contentReference[oaicite:8]{index=8}.
5. **Arquitetura em Camadas (Layered System)**: O cliente não sabe se está comunicando com o servidor diretamente ou via intermediários (proxies, gateways etc.) :contentReference[oaicite:9]{index=9}.
6. **Código Sob Demanda (Code-on-Demand)** – opcional: o servidor pode enviar código executável ao cliente, como scripts ou applets :contentReference[oaicite:10]{index=10}.

## 4. Métodos HTTP e Operações CRUD

| Método HTTP | Operação CRUD        | Descrição                                          |
|-------------|-----------------------|----------------------------------------------------|
| GET         | Read / Retrieve       | Recupera dados do recurso                          |
| POST        | Create                | Cria novo recurso                                  |
| PUT         | Update / Replace      | Altera ou cria o recurso (substituição completa)   |
| PATCH       | Update parcial        | Atualiza parcialmente um recurso existente         |
| DELETE      | Delete                | Remove um recurso                                  |

Esses métodos são usados para manipular recursos sobre HTTP e retornam códigos de status adequados (como 200, 201, 404 etc.) :contentReference[oaicite:11]{index=11}.

## 5. Formatos de Representação

- **JSON**: o formato mais comum pela legibilidade e compatibilidade com diversas linguagens :contentReference[oaicite:12]{index=12}.
- Também podem ser usados XML, YAML, HTML, texto puro etc., conforme o media type definido para o recurso :contentReference[oaicite:13]{index=13}.

## 6. HATEOAS (Hypermedia as the Engine of Application State)

- Uma API RESTful verdadeiramente sofisticada inclui **links de navegação** nos recursos, permitindo que o cliente descubra ações disponíveis sem precisar conhecer previamente todos os endpoints :contentReference[oaicite:14]{index=14}.
- As possíveis operações mudam conforme o estado de cada recurso – um exemplo clássico é uma conta bancária com links para depósitos, retiradas ou encerramentos dependendo do saldo :contentReference[oaicite:15]{index=15}.

## 7. Vantagens das APIs RESTful

- **Leveza e eficiência**: menos overhead comparado a SOAP ou RPC :contentReference[oaicite:16]{index=16}.
- **Independência tecnológica**: APIs REST podem ser implementadas em qualquer linguagem ou plataforma :contentReference[oaicite:17]{index=17}.
- **Escalabilidade e modularidade**: design sem estado e arquitetura em camadas ajudam na escalabilidade :contentReference[oaicite:18]{index=18}.
- **Padronização e previsibilidade**: convenções claras para URIs, métodos HTTP e status codes.

## 8. Quando REST não é REST “puro”?

Nem toda API que usa HTTP+JSON é estritamente RESTful. Fatores como ausência de HATEOAS ou uso de sessões quebram algumas das restrições do REST arquitetônico :contentReference[oaicite:19]{index=19}.  
APIs que satisfazem parcialmente os princípios geralmente são chamadas de “acidentalmente RESTful” :contentReference[oaicite:20]{index=20}.

---

## 📄 Resumo rápido

- **REST** é um estilo arquitetural fundamentado em recursos identiﬁcáveis, troca de representações via HTTP e seis restrições principais.
- É baseado em **URLs**, **métodos HTTP padrão**, **formatos como JSON**, e idealmente segue o modelo **HATEOAS**.
- **RESTful APIs** são amplamente utilizadas por sua simplicidade, flexibilidade, escalabilidade e interoperabilidade.