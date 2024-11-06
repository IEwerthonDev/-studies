# 🔍 Unit Testing

### O que é?

**Unit Testing** (ou Teste Unitário) é um tipo de teste onde verificamos o funcionamento de partes isoladas e pequenas da aplicação, chamadas de "unidades". Geralmente, essas unidades são funções, métodos ou classes individuais. O objetivo é garantir que cada unidade funcione corretamente de forma independente, antes de testá-la em um sistema mais complexo.

### Como Funciona?

Um teste unitário é escrito para validar que uma função ou método retorne o resultado esperado para um conjunto de entradas. Em PHP, frameworks como **PHPUnit** facilitam a criação e execução de testes unitários.

### Exemplo em PHP (PHPUnit)

```php
// Arquivo Calculator.php
class Calculator {
    public function add($a, $b) {
        return $a + $b;
    }
}

// Arquivo CalculatorTest.php
use PHPUnit\Framework\TestCase;

class CalculatorTest extends TestCase {
    public function testAdd() {
        $calculator = new Calculator();
        $this->assertEquals(4, $calculator->add(2, 2));
        $this->assertEquals(0, $calculator->add(2, -2));
    }
}
```

---

Neste exemplo, criamos uma classe `Calculator` com um método `add`. No teste, verificamos se o método `add` está retornando o valor esperado para diferentes entradas.

Para executar, você rodaria o comando:

~~~bash
phpunit CalculatorTest.php
~~~