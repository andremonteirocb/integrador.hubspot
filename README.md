# HUBSPOT
.NET Class Library for integration with HUBSPOT API <br />
.Net Framework 4.6.1

### Adicione as chaves no web.config
```c#
  <add key="user:hapikey" value="_hapikey_do_cliente_hubspot" />
  <add key="app:urlforms" value="https://api.hsforms.com" />
  <add key="app:url" value="https://api.hubapi.com" />
  ```
### Criar engagement
```c#
using(var hubspot = new HubSpot())
{
    hubspot.Engagement.CriarEngagement(contactId, mensagem);
}
```

### Obter produto pelo id
```c#
using(var hubspot = new HubSpot())
{
  var produto = hubSpot.Product.RecuperarProdutoById(productId);
}
```

### Obter todos os produtos
```c#
using(var hubspot = new HubSpot())
{
  var produtos = hubSpot.Product.RecuperarTodosOsProdutos();
}
```

### Criar produto
```c#
using(var hubspot = new HubSpot())
{
  var dados = new DadosIntegracao
  {
      Deal = new DadosDeal
      {
          Propriedades = new List<Propriedade> 
          {
              new Rest.Models.Propriedade { Chave = "chave", Valor = "valor" },
              new Rest.Models.Propriedade { Chave = "recurringbillingfrequency", Valor = "per_six_months" }
          }
      }
  };
  var produto = hubSpot.Product.CriarProduto(dados);
}
```

### Atualizar produto
```c#
using(var hubspot = new HubSpot())
{
  var dados = new DadosIntegracao
  {
      Deal = new DadosDeal
      {
          Propriedades = new List<Propriedade> 
          {
              new Rest.Models.Propriedade { Chave = "chave", Valor = "novo_valor" },
              new Rest.Models.Propriedade { Chave = "recurringbillingfrequency", Valor = "per_six_months" }
          }
      }
  };
  var produto = hubSpot.Product.AtualizarProduto(dados);
}
```

### Deletar produto
```c#
using(var hubspot = new HubSpot())
{
  hubSpot.Product.DeletarProduto(productId);
}
```

### Obter pipeline pelo id
```c#
using(var hubspot = new HubSpot())
{
  hubSpot.Pipeline.RecuperarTodosOsPipelines();
}
```

### Obter todos os pipelines
```c#
using(var hubspot = new HubSpot())
{
  hubSpot.Pipeline.RecuperarPipelineComDealStages(pipelineId);
}
```

### Obter requests do dia
```c#
using(var hubspot = new HubSpot())
{
  var integration = hubSpot.Integrations.RecuperarNumeroDeRequestDiarioDaApi();
}
```

### Enviar formulário
```c#
using(var hubspot = new HubSpot())
{
  var dados = new DadosIntegracao
  {
      Deal = new DadosFormulario
      {
          PortalId = "portal_id",
          FormId = "form_id",
          Contexto = new ContextForm 
          {
            CookieHubSpot = "cookie",
            PageUri = "page_uri",
            IpAddress = "ip_address",
            PageName = "page_name"
          },
          Propriedades = new List<Propriedade> 
          {
              new Rest.Models.Propriedade { Chave = "chave", Valor = "valor" }
          }
      }
  };
  //skipValidation ignorar erros caso true
  var form = _hubSpot.Form.EnviarFormulario(dados, skipValidation);
}
```
