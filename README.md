# Temperature Monitoring System - Sistema de Monitoramento de Temperatura e Condições Ambientais

A **Temperature Monitoring System** é uma aplicação web desenvolvida em **ASP.NET Core MVC** com foco no monitoramento de temperatura e condições ambientais. O projeto foi estruturado para organizar usuários, sensores, tipos de sensores e o vínculo entre eles, utilizando **SQL Server** como banco de dados.

## Descrição para o GitHub
Aplicação web em ASP.NET Core MVC para monitoramento ambiental, com gerenciamento de usuários, sensores e tipos de sensores, integrada ao SQL Server.

## Objetivo
O objetivo deste projeto é servir como base para um sistema de monitoramento ambiental capaz de:

- cadastrar usuários;
- cadastrar sensores;
- organizar tipos de sensores;
- relacionar usuários aos sensores monitorados;
- preparar a base para consultas e relatórios sobre medições e monitoramento.

## Tecnologias utilizadas

- C#
- ASP.NET Core MVC
- .NET Core 3.1
- SQL Server
- System.Data.SqlClient
- Razor Views

## Estrutura do projeto

```text
SiteMonitoramentoTemp/
├── BancoDeDados/
│   ├── TabelasBancoDeDados.sql
│   └── TipoSensoresInsert.sql
└── SiteMonitoramento/
    ├── Controllers/
    ├── DAO/
    ├── Models/
    ├── Views/
    ├── Program.cs
    ├── Startup.cs
    ├── appsettings.json
    └── SiteMonitoramento.csproj
````

## Funcionalidades existentes

### Camada de dados

O projeto possui classes DAO para manipulação das entidades principais:

* Usuários
* Sensores
* Tipos de sensores
* Usuário x Sensor

Essas classes já implementam operações como:

* inserção;
* alteração;
* exclusão;
* consulta por ID;
* listagem.

Também existe uma consulta com **JOIN** para retornar dados consolidados entre usuário e sensor.

### Banco de dados

O diretório `BancoDeDados` contém scripts para:

* criação das tabelas principais;
* inserção inicial de tipos de sensores.

Exemplos de sensores previstos no projeto:

* DHT22
* DHT11
* FotoSensor
* RTC
* DHT33

### Interface

A aplicação possui páginas Razor organizadas em views como:

* `Home`
* `Usuario`
* `Sensor`

Além disso, há uma página institucional **Sobre**, apresentando a proposta da Temperature Monitoring System como solução de monitoramento de temperatura e umidade.

## Modelagem básica

As principais entidades do sistema são:

### Usuario

Representa o usuário do sistema.

Campos principais:

* `UsuarioId`
* `UsuarioNome`
* `Senha`
* `Email`
* `CPF`

### Sensor

Representa um sensor cadastrado no sistema.

Campos principais:

* `SensorId`
* `SensorNome`
* `TipoSensorId`

### TipoSensor

Representa a categoria técnica do sensor.

Campos principais:

* `TipoSensorId`
* `NomeTecnico`
* `ParametroMedido`

### UsuarioSensor

Representa o vínculo entre um usuário e um sensor.

Campos principais:

* `UsuarioSensorId`
* `UsuarioId`
* `SensorId`

## Como configurar o projeto

### 1. Clonar o repositório

```bash
git clone https://github.com/nicholasbirochi/SiteMonitoramentoTemp.git
```

### 2. Configurar o banco de dados

Crie um banco SQL Server com o nome desejado e execute os scripts na seguinte ordem:

1. `BancoDeDados/TabelasBancoDeDados.sql`
2. `BancoDeDados/TipoSensoresInsert.sql`

### 3. Ajustar a conexão com o banco

A conexão com o banco está definida na classe `ConexaoBD.cs`.

Exemplo de string de conexão usada no projeto:

```csharp
Data Source=LOCALHOST;Initial Catalog=SiteMonitoramentoSensores;User Id=sa;Password=123456;TrustServerCertificate=True;
```

Altere esses dados conforme o seu ambiente local.

### 4. Restaurar dependências

```bash
dotnet restore
```

### 5. Executar a aplicação

```bash
dotnet run
```

## Rotas principais

A rota padrão do projeto está configurada para:

```text
/Home/Index
```

Também existe a página:

```text
/Home/Sobre
```

## Melhorias futuras

Algumas evoluções que podem ser aplicadas ao projeto:

* mover a string de conexão para `appsettings.json`;
* implementar autenticação e autorização;
* criar controllers completos para usuários e sensores;
* adicionar dashboard com gráficos e histórico de medições;
* integrar sensores reais ou APIs de coleta;
* aplicar Entity Framework Core ou um padrão de repositório;
* melhorar validações e tratamento de erros.

## Observações

Este projeto é uma boa base para estudos de:

* ASP.NET Core MVC;
* arquitetura em camadas;
* acesso a dados com ADO.NET;
* integração com SQL Server;
* sistemas de monitoramento ambiental.

## Autor

Projeto mantido por **Nicholas Birochi**.
