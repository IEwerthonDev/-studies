# 🔗 Integration Testing

### O que é?

**Integration Testing** (ou Teste de Integração) é um tipo de teste que verifica se diferentes partes de um sistema funcionam corretamente em conjunto. O objetivo é testar a interação entre unidades ou módulos que foram previamente testados individualmente em testes unitários.

### Como Funciona?

Os testes de integração são utilizados para validar a comunicação entre diferentes partes do sistema. Em um sistema web, isso poderia significar testar a interação entre o backend e o banco de dados, ou entre uma API e o frontend. No PHP, o PHPUnit também é amplamente utilizado para testes de integração.

### Exemplo em PHP (Teste de Integração com Banco de Dados)

Neste exemplo, vamos supor que tenhamos uma aplicação que se conecta a um banco de dados para adicionar e buscar dados de usuários.

```php
// Arquivo User.php
class User {
    private $db;

    public function __construct(PDO $db) {
        $this->db = $db;
    }

    public function createUser($name, $email) {
        $stmt = $this->db->prepare("INSERT INTO users (name, email) VALUES (:name, :email)");
        $stmt->bindParam(':name', $name);
        $stmt->bindParam(':email', $email);
        return $stmt->execute();
    }

    public function getUserByEmail($email) {
        $stmt = $this->db->prepare("SELECT * FROM users WHERE email = :email");
        $stmt->bindParam(':email', $email);
        $stmt->execute();
        return $stmt->fetch();
    }
}

// Arquivo UserTest.php
use PHPUnit\Framework\TestCase;

class UserTest extends TestCase {
    private $db;
    private $user;

    protected function setUp(): void {
        $this->db = new PDO('sqlite::memory:');
        $this->db->exec("CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT, email TEXT)");
        $this->user = new User($this->db);
    }

    public function testCreateAndRetrieveUser() {
        $this->user->createUser('John Doe', 'john@example.com');
        $user = $this->user->getUserByEmail('john@example.com');
        $this->assertEquals('John Doe', $user['name']);
        $this->assertEquals('john@example.com', $user['email']);
    }
}
```

Neste exemplo, o teste cria um usuário e depois verifica se ele foi armazenado e recuperado corretamente do banco de dados.

Para executar o teste:
```bash
phpunit UserTest.php
```