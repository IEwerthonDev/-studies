# **Memcached**
Memcached é outra solução de cache em memória, conhecida por sua simplicidade e eficiência. Ele é usado principalmente para armazenar pares de chave-valor simples, sendo uma escolha popular para reduzir a carga no banco de dados em aplicações de grande escala.

Exemplo de uso com PHP:
   ```php
   // Conectar ao Memcached
   $memcached = new Memcached();
   $memcached->addServer('127.0.0.1', 11211);

   // Armazenar valor em cache
   $memcached->set('chave', 'valor');

   // Obter valor em cache
   $valor = $memcached->get('chave');
   echo $valor; // Output: valor
   ```
---

Usar o Memcached como cache para dados reduz a carga no banco de dados e melhora o tempo de resposta da aplicação. Aqui, vamos configurar o cache para armazenar dados do banco de dados temporariamente.

### Exemplo de Implementação com PHP e Memcached

```php
// Conectar ao Memcached
$memcached = new Memcached();
$memcached->addServer('127.0.0.1', 11211);

// Definir a chave e o tempo de expiração do cache
$cacheKey = 'usuarios_dados';
$cacheTime = 600; // Cache de 10 minutos

// Tentar obter dados do cache
$dadosUsuarios = $memcached->get($cacheKey);

if ($dadosUsuarios === false) {
    // Se não está no cache, buscar dados do banco de dados
    $pdo = new PDO('mysql:host=localhost;dbname=seu_banco', 'usuario', 'senha');
    $stmt = $pdo->query("SELECT id, nome, email FROM usuarios");
    $dadosUsuarios = $stmt->fetchAll(PDO::FETCH_ASSOC);

    // Armazenar dados no Memcached
    $memcached->set($cacheKey, $dadosUsuarios, $cacheTime);
}

// Exibir dados
foreach ($dadosUsuarios as $usuario) {
    echo "Nome: " . $usuario['nome'] . " | Email: " . $usuario['email'] . "<br>";
}
```

Esse código primeiro verifica se os dados dos usuários estão no cache. Caso contrário, ele consulta o banco de dados e armazena o resultado no Memcached para uso futuro, com uma expiração de 10 minutos.