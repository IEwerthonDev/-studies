# ✅ Functional Testing

### O que é?

**Functional Testing** (ou Teste Funcional) é um tipo de teste que verifica se uma funcionalidade específica do sistema está funcionando conforme o esperado. Diferente dos testes unitários e de integração, que são mais técnicos, o teste funcional é focado na experiência do usuário, garantindo que cada funcionalidade corresponda aos requisitos.

### Como Funciona?

Um teste funcional é executado simulando as ações do usuário e verificando se o sistema responde corretamente. Para aplicações web, ferramentas como **Selenium** e **Codeception** (para PHP) podem ser utilizadas para realizar testes funcionais.

### Exemplo com Codeception (PHP)

Usando Codeception, podemos simular o acesso do usuário a uma página de login e verificar se ele consegue efetuar o login com sucesso.

```php
// Arquivo de teste LoginCest.php
class LoginCest {
    public function _before(\AcceptanceTester $I) {
        // Pré-condições para o teste, como abrir o navegador na URL de teste
        $I->amOnPage('/login');
    }

    public function loginWithValidCredentials(\AcceptanceTester $I) {
        $I->fillField('username', 'usuario_exemplo');
        $I->fillField('password', 'senha_exemplo');
        $I->click('Entrar');
        $I->see('Bem-vindo, usuario_exemplo');
    }

    public function loginWithInvalidCredentials(\AcceptanceTester $I) {
        $I->fillField('username', 'usuario_invalido');
        $I->fillField('password', 'senha_errada');
        $I->click('Entrar');
        $I->see('Credenciais inválidas');
    }
}
```

No exemplo acima, temos um teste funcional que simula o login do usuário. Ele verifica se o sistema responde corretamente tanto com credenciais válidas quanto inválidas.

Para executar os testes com Codeception:
```bash
codecept run
```
