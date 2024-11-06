# 🖥️ **Server Side Caching (Cache no Lado do Servidor)**
O cache no lado do servidor envolve armazenar dados diretamente no servidor para melhorar a performance de respostas. Isso pode incluir o uso de Redis ou Memcached para armazenar dados temporários, reduzindo a carga de processamento ao evitar operações repetitivas.

Para fazer o caching no lado do servidor (Server Side Caching) da forma mais robusta, vamos usar uma combinação de:

1. **Redis** para armazenar os dados em memória com expiração definida.
2. **Banco de Dados Relacional** (como MySQL ou PostgreSQL) como fonte primária dos dados.

Neste exemplo, o processo será o seguinte:

- Primeiro, verificaremos se os dados estão em cache (Redis).
- Se os dados estiverem em cache e ainda forem válidos, retornaremos esses dados para evitar uma consulta ao banco de dados.
- Se os dados **não** estiverem em cache ou se o cache tiver expirado, faremos uma consulta ao banco de dados e então armazenaremos os resultados no cache para requisições futuras.

### Estrutura da Tabela no Banco de Dados

Primeiro, imagine que temos uma tabela de `usuarios` que queremos acessar e cachear. A estrutura da tabela pode ser algo assim:

```sql
CREATE TABLE usuarios (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100),
    email VARCHAR(100)
);
```

### Configuração do Redis

Redis deve estar rodando em um servidor (local ou remoto) para que o PHP possa se conectar a ele. Vamos usar Redis para armazenar uma versão cacheada dos dados dos usuários.

### Implementação Completa em PHP para Server Side Caching

Este código PHP faz o seguinte:

1. Tenta buscar os dados no Redis.
2. Se os dados não estão no Redis, ele consulta o banco de dados, salva os dados no cache Redis com uma expiração e, em seguida, retorna os dados.

#### Exemplo de Código em PHP

```php
// Conectar ao Redis
$redis = new Redis();
$redis->connect('127.0.0.1', 6379);

// Configurações do cache
$cacheKey = 'usuarios_dados';
$cacheTime = 600; // Expiração do cache em segundos (10 minutos)

// Tentar obter dados do Redis
$dadosUsuarios = $redis->get($cacheKey);

if ($dadosUsuarios) {
    // Se os dados estão no cache, decodificar o JSON
    $dadosUsuarios = json_decode($dadosUsuarios, true);
} else {
    // Se não há cache, buscar dados do banco de dados
    $pdo = new PDO('mysql:host=localhost;dbname=seu_banco', 'usuario', 'senha');
    $stmt = $pdo->query("SELECT id, nome, email FROM usuarios");
    $dadosUsuarios = $stmt->fetchAll(PDO::FETCH_ASSOC);

    // Armazenar dados no Redis em formato JSON
    $redis->setex($cacheKey, $cacheTime, json_encode($dadosUsuarios));
}

// Exibir dados dos usuários
foreach ($dadosUsuarios as $usuario) {
    echo "Nome: " . $usuario['nome'] . " | Email: " . $usuario['email'] . "<br>";
}
```

### Explicação do Código

1. **Conexão com Redis**: Estabelecemos a conexão com o Redis em `127.0.0.1` na porta padrão `6379`.
2. **Tentativa de Obter Dados do Cache**:
    - Usamos a chave `usuarios_dados` para verificar se os dados já estão armazenados em Redis.
    - Se `get()` retornar um valor, significa que o cache está disponível, e os dados são decodificados de JSON para array PHP.
3. **Consulta ao Banco de Dados**:
    - Se o cache não existir ou tiver expirado, uma consulta SQL é feita para buscar os dados dos usuários no banco de dados.
4. **Armazenamento no Cache**:
    - Após recuperar os dados do banco de dados, armazenamos no Redis usando `setex()`, que permite definir uma chave com um tempo de expiração.
    - O `cacheTime` de 600 segundos significa que os dados serão armazenados por 10 minutos antes de expirar.
5. **Exibição dos Dados**:
    - Finalmente, os dados dos usuários são exibidos, independentemente de virem do cache ou diretamente do banco de dados.

### Vantagens dessa Abordagem

- **Eficiência**: Consultas repetidas ao banco de dados são evitadas, economizando tempo e recursos do servidor.
- **Expiração Automática**: O uso de `setex` no Redis permite que os dados expirem automaticamente após o período especificado.
- **Escalabilidade**: Redis, sendo um armazenamento em memória de alto desempenho, é muito eficiente para armazenar dados frequentemente acessados, mesmo em aplicações de grande escala.

---

### Configuração Extra: Invalidação do Cache

Em uma aplicação real, pode ser necessário invalidar o cache quando os dados são atualizados no banco de dados. Para isso, sempre que uma operação de inserção, atualização ou exclusão é feita no banco de dados, você pode remover ou atualizar o cache correspondente no Redis.

Exemplo de remoção do cache:

```php
$redis->del('usuarios_dados'); // Remove o cache com a chave especificada
```

Após a remoção do cache, na próxima vez que os dados forem solicitados, o cache será reconstruído com os dados atualizados do banco.

---

Essa implementação de **Server Side Caching** usando **Redis** e **banco de dados** como fonte principal é uma abordagem prática e eficiente para melhorar a performance e escalabilidade de aplicações PHP.