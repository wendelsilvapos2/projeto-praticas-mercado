
# Projeto Aplicado - Práticas de Mercado

## Sobre o Projeto

Este projeto foi desenvolvido como atividade da disciplina **Projeto Aplicado: Práticas de Mercado**, com foco em práticas de desenvolvimento seguro, hospedagem em nuvem e automação de deploy.

A aplicação consiste em um sistema Web desenvolvido em Laravel contendo:

- Login de usuários
- Área interna protegida
- Logout
- Controle de sessão
- Hospedagem em ambiente Cloud

---

## Endereços do Projeto

### Aplicação

https://wendelsilvapos.duckdns.org

### Repositório GitHub

https://github.com/wendelsilvapos2/projeto-praticas-mercado

---

## Tecnologias Utilizadas

- Laravel 13
- PHP 8.5
- SQLite
- Nginx
- Ubuntu Server
- AWS EC2
- GitHub Actions
- DuckDNS
- Fail2Ban
- Let's Encrypt SSL

---

## Funcionalidades

### Login

Permite autenticação de usuários utilizando e-mail e senha.

### Área Protegida

Acesso restrito apenas para usuários autenticados.

### Logout

Encerramento seguro da sessão do usuário.

---

## Infraestrutura

### Servidor

- AWS EC2
- Ubuntu Server

### Servidor Web

- Nginx

### Segurança

- Acesso SSH por chave criptográfica
- Fail2Ban configurado na porta SSH
- SSL/TLS com Let's Encrypt
- Redirecionamento HTTP → HTTPS

---

## Integração Contínua e Entrega Contínua (CI/CD)

O projeto utiliza GitHub Actions para automatizar o processo de deploy.

Fluxo:

Desenvolvimento Local

↓

GitHub

↓

GitHub Actions

↓

Servidor EC2

↓

Produção

---

# OWASP Top 10 - Controles de Segurança Implementados

## A01 - Broken Access Control (Falhas de Controle de Acesso)

As rotas protegidas da aplicação utilizam o middleware de autenticação do Laravel.

Somente usuários autenticados conseguem acessar páginas internas.

Exemplo:

```php
Route::middleware('auth')->group(function () {
    Route::get('/dashboard');
});
```

### Mitigações Implementadas

- Middleware auth
- Controle de sessão
- Redirecionamento para login
- Restrição de acesso a áreas protegidas

---

## A02 - Cryptographic Failures (Falhas Criptográficas)

As senhas não são armazenadas em texto puro.

O Laravel utiliza bcrypt para armazenamento seguro das credenciais.

Exemplo:

```php
Hash::make($password);
```

### Mitigações Implementadas

- Senhas criptografadas
- HTTPS com SSL/TLS
- Sessões protegidas

---

## A03 - Injection (Injeção)

A aplicação utiliza validação de entrada e Eloquent ORM.

Exemplo:

```php
$request->validate([
    'email' => 'required|email',
    'password' => 'required'
]);
```

### Mitigações Implementadas

- Validação dos dados enviados pelo usuário
- Eloquent ORM
- Proteção contra SQL Injection
- Sanitização das entradas

---

## Segurança Implementada no Projeto

- HTTPS
- Fail2Ban
- Chave SSH
- Middleware de autenticação
- Controle de sessão
- Senhas criptografadas
- Proteção contra SQL Injection
- GitHub Secrets
- CI/CD automatizado

---

## Estrutura do Projeto

```text
app/
bootstrap/
config/
database/
public/
resources/
routes/
storage/
```

---

## Autor

Wendel Silva

Projeto desenvolvido para fins acadêmicos na disciplina Projeto Aplicado: Práticas de Mercado.
