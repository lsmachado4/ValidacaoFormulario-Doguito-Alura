# Validações de formulários

## Atributos de validação (HTML)

Passamos como atributo `required` na tag `input ` para que o/a usuário(a) não envie um valor do campo como vazio no arquivo `cadastro.html`

```html

<input name="nome" id="nome" class="input" type="text" placeholder="Nome" required>
```

## Email
No campo de **email** utiliza-se, além do `required`, o atributo `type="email"`, garantindo que o tipo de entrada preenchido pelo(a) usuário(a)  mantenha a estrutura básica de email (ex.: _usuario@email.com_), então sendo: 

```html
<input name="email" id="email" class="input" type="email" placeholder="Email" required>
```
## Senha

Analogamente ao email, para o campo de senha, utilizamos `type="password"`para ocultar os caracteres da senha, sendo assim: 

<br>

```html
<input name="senha" id="senha" class="input" type="password" placeholder="Senha" required>
```
<br>

Para garantir que o/a usuário(a) digite a quantidade mínima de caracteres utiliza-se o atributo `minlength=""`. O código fica assim: 


```html
<input name="senha" id="senha" class="input" type="password" placeholder="Senha" minlength="6" required>
```

## Atributo patten utilizando Regex

Outra forma de validação é utilizar o atributo `Pattern` para receber uma expressão regular (RegEx), que são padrões para identificar combinação. Na comunidade [RegexLib](https://regexlib.com/Search.aspx?k=passwo&AspxAutoDetectCookieSupport=1) ou [Regexr.com](https://regexr.com/) podemos encontrar mais dessas expressões. 

O aplicamos a seguinte validação: 
```html
<!-- Início da expressão regular -->
pattern="^


<!-- 1ª condição: permitido letras minúsculas nesse intervalo -->
(?=.*[a-z])   

<!-- 2ª condição: permitido letras maiúsculas-->  
(?=.*[A-Z])     

<!-- 3ª condição: permitido o intervalo numérico -->
(?=.*[0-9]) 
 
 <!-- 4ª condição: não é permitido esses caracteres especiais -->    
(?!.*[!@#$%^&*_=+-:,]) 

<!-- Intervalos de caracteres -->
.{6,12}    
<!-- Fechamento da expressão regular -->
$"

```
o código fica assim: 

```html
<input name="senha" id="senha" class="input" type="password" placeholder="Senha"pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?!.*[!@#$%^&*_=+-:,]).{6,12}$" required>
```

Para passar a a mensagem informando ao usuário(a) a descrição de qual deve ser a estrutura da senha, utiliza-se o atribulo `title`, ficando: 

```html
<input name="senha" id="senha" class="input" type="password" placeholder="Senha"pattern="^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?!.*[!@#$%^&*_=+-:,]).{6,12}$" title="A senha deve conter entre 6 e 12 caracteres, deve conter pelo menos uma letra maiúscula, um número e não deve conter símbolos" required>

```
Lembrando que esse artifício é uma possibilidade válida, mas que por questões de boas práticas, o indicado é que as chamadas de erros sejam executadas dinamicamente dentro do arquivo JavaScript. 