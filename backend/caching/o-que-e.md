# 🗃️ Caching

**Caching** é uma técnica de otimização que armazena dados temporariamente para acesso rápido em uma camada intermediária, conhecida como **cache**. A ideia principal do caching é evitar o processamento repetido de informações que mudam com pouca frequência ou que são caras em termos de tempo e recursos para serem recuperadas.

Em uma aplicação web, caching pode ser aplicado em diferentes camadas, como:

- **Cache no lado do servidor**: armazenando dados frequentemente acessados diretamente no servidor, reduzindo consultas a bancos de dados ou outras operações repetitivas.
- **Cache de conteúdo**: usando redes de entrega de conteúdo (CDNs) para armazenar arquivos estáticos em locais mais próximos do usuário.
- **Cache no lado do cliente**: armazenando conteúdo no dispositivo do usuário (como em navegadores) para reduzir o tempo de carregamento.

Essa técnica é essencial para melhorar a **performance** e **escalabilidade** de sistemas, permitindo respostas mais rápidas e reduzindo a carga nos servidores e banco de dados.

---

Com essa base, podemos entender como os diferentes tipos de cache (Redis, Memcached, CDN, etc.) contribuem para a eficiência de uma aplicação web, como detalhado anteriormente.