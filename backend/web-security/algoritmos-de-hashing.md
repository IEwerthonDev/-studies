# 🥢 Algoritmos de Hashing

Os algoritmos de hashing são utilizados para converter dados (como senhas) em uma sequência fixa de caracteres (hash), que não pode ser revertida para o valor original. Isso é especialmente útil para armazenar senhas de forma segura em uma base de dados. Vamos ver alguns algoritmos de hashing comuns:

### MD5

O **MD5** (Message Digest Algorithm 5) gera um hash de 128 bits (32 caracteres hexadecimais) a partir de uma entrada. Embora ainda seja utilizado, o MD5 não é mais considerado seguro para armazenar senhas, pois é vulnerável a ataques de colisão.

```php
$senha = "minha_senha_secreta";
$hash_md5 = md5($senha);
echo "Hash MD5: " . $hash_md5;
```

### SHA (Secure Hash Algorithm)

SHA é uma família de algoritmos de hash. Os mais comuns são **SHA-1**, **SHA-256** e **SHA-512**. O SHA-1 é mais antigo e vulnerável, mas SHA-256 e SHA-512 ainda são considerados seguros.

```php
$senha = "minha_senha_secreta";
$hash_sha256 = hash('sha256', $senha);
echo "Hash SHA-256: " . $hash_sha256;
```

### scrypt

O **scrypt** é um algoritmo de hashing com maior resistência a ataques de força bruta, pois requer uma quantidade significativa de memória para ser executado, dificultando a quebra do hash. Ele é amplamente utilizado em criptomoedas, mas também pode ser usado para proteger senhas.

> No PHP, `scrypt` não é nativamente suportado, mas você pode usar bibliotecas específicas ou outras linguagens que suportam diretamente o algoritmo.

### bcrypt

**bcrypt** é um algoritmo de hashing adaptável, o que significa que ele permite configurar a "força" do hash com um custo computacional. Ele é amplamente utilizado para o armazenamento seguro de senhas.

```php
$senha = "minha_senha_secreta";
$hash_bcrypt = password_hash($senha, PASSWORD_BCRYPT);
echo "Hash bcrypt: " . $hash_bcrypt;

// Verificação de senha com bcrypt
$verificar = password_verify($senha, $hash_bcrypt);
echo "Senha válida? " . ($verificar ? "Sim" : "Não");
```