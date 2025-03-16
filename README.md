# 📌 Como Utilizar o LatinosSecurity no teu Servidor FiveM

Este guia fornece instruções detalhadas sobre como integrar e utilizar o **LatinosSecurity** no teu servidor **FiveM**.

---

## 🚀 Instalação e Configuração

1. Certifica-te de que o **LatinosSecurity** está corretamente instalado no teu servidor.
2. Adiciona a dependência ao teu recurso:
   ```lua
   ensure LatinosSecurity
   ```
3. Utiliza os eventos e callbacks protegidos conforme explicado abaixo.

---

## 🔐 Eventos Protegidos

Os eventos protegidos são registados e chamados da seguinte maneira:

### 🔹 **Server Side**

Para registar um evento protegido no servidor, utiliza:

```lua
exports["LatinosSecurity"]:RegisterServerEvent("meuEvento", function(source, valor)
    print("Recebido do cliente: " .. valor)
end)
```

⚠ **Importante:** O parâmetro `source` **deve** estar no início da função, caso contrário, o evento **não funcionará**.

### 🔹 **Client Side**

Para acionar um evento protegido do lado do cliente, utiliza:

```lua
exports["LatinosSecurity"]:TriggerServerEvent("meuEvento", "Olá, servidor!")
```

---

## 🔄 Callbacks Protegidas

As callbacks protegidas garantem segurança ao retorno de dados entre o servidor e o cliente.

### 🔹 **Server Side**

Para registar uma callback protegida no servidor, utiliza:

```lua
exports["LatinosSecurity"]:RegisterServerCallback("pegarItem", function(source, item)
    local quantidade = math.random(1, 10)
    return item .. "_" .. quantidade
end)
```

⚠ **Importante:** O parâmetro `source` **deve** estar no início da função, caso contrário, a callback **não funcionará**.

➡ **Para enviar a informação para o Client Side, é necessário dar `return` no final da função.**

### 🔹 **Client Side**

Para chamar uma callback protegida do lado do cliente, utiliza:

```lua
exports["LatinosSecurity"]:TriggerServerCallback("pegarItem", function(resultado)
    print("Item recebido: " .. resultado)
end, "medkit")
```

---

## 📌 Notas Finais

- Certifica-te de que o **LatinosSecurity** está a correr corretamente no servidor.
- Garante que segues a estrutura correta dos eventos e callbacks para evitar erros.
- Para suporte adicional, consulta a documentação oficial ou entra em contacto com a equipa responsável.

✨ **Agora estás pronto para utilizar o LatinosSecurity no teu servidor FiveM com segurança e eficiência!**
