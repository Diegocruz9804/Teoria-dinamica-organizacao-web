A **validação de formulários no lado do cliente** usando JavaScript é uma etapa fundamental para garantir que os dados inseridos pelo usuário estejam corretos **antes** de serem enviados ao servidor. Isso melhora a experiência do usuário, evita sobrecarregar o servidor com dados inválidos e reduz erros.

Quando um usuário preenche um formulário em uma página web, o JavaScript pode capturar os dados inseridos e verificar se eles seguem certos critérios — como campos obrigatórios, formatos específicos (como e-mail ou CPF), ou limites de caracteres. Essa validação acontece diretamente no navegador, **sem a necessidade de recarregar a página ou acessar o servidor**.

Para isso, o JavaScript se conecta a eventos do formulário, como o `onsubmit` (quando o formulário é enviado), ou `oninput` (quando o usuário digita). Ele pode então acessar os valores dos campos com `document.getElementById()` ou `document.querySelector()` e verificar o que foi digitado usando **condições lógicas** ou **expressões regulares**.

Por exemplo, suponha que você tenha um formulário com um campo de e-mail. O JavaScript pode acessar o valor digitado assim:

```javascript
const email = document.getElementById("email").value;
```

Depois, ele pode verificar se o campo está vazio ou se o texto corresponde a um formato válido de e-mail. Para validações mais avançadas, é comum usar **expressões regulares**, que são padrões usados para testar se uma string segue um formato esperado.

Uma **expressão regular (regex)** é uma sequência de caracteres que define um padrão de busca. Com ela, é possível verificar se um texto possui letras, números, símbolos específicos, quantidade mínima de caracteres, entre outros.

Veja um exemplo de validação de e-mail com JavaScript e regex:

```html
<form onsubmit="return validarFormulario()">
  <label>Email:</label>
  <input type="text" id="email" />
  <input type="submit" value="Enviar" />
</form>

<script>
  function validarFormulario() {
    const email = document.getElementById("email").value;

    // Expressão regular para validar e-mails
    const regexEmail = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

    if (!regexEmail.test(email)) {
      alert("Por favor, insira um e-mail válido.");
      return false; // Impede o envio do formulário
    }

    return true; // Permite o envio se estiver válido
  }
</script>
```

Essa expressão `/^[^\s@]+@[^\s@]+\.[^\s@]+$/` funciona assim:

* `^` e `$` marcam o início e o fim da string (ou seja, o texto todo deve obedecer à regra).
* `[^\s@]+` significa "um ou mais caracteres que **não** sejam espaço (`\s`) nem arroba (`@`)" — usado para a parte do nome do e-mail.
* `@` é o símbolo obrigatório de todo e-mail.
* `[^\s@]+` novamente, agora para o domínio (ex: `gmail`).
* `\.` representa o ponto (ponto precisa ser escapado com `\` porque tem outro significado em regex).
* `[^\s@]+` valida o final do domínio (ex: `com`, `org`, `net` etc.).

Esse padrão cobre a maioria dos e-mails válidos, mas você pode usar expressões mais complexas dependendo do nível de exigência.

Em resumo, o JavaScript permite capturar os valores de um formulário, validá-los com regras personalizadas e expressões regulares, e impedir o envio se os dados estiverem incorretos. Isso melhora tanto a segurança quanto a usabilidade do site.

Se quiser, posso te mostrar um exemplo completo com nome, e-mail e senha, tudo validado em tempo real.
