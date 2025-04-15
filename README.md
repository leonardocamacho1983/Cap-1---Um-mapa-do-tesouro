# Cap-1---Um-mapa-do-tesouro
[Uploading Cap-1---Um-mapa-do-tesouro.ddl…]()

Vou elaborar o texto para o MER (Modelo Entidade-Relacionamento) com base no arquivo SQL exportado. Este texto servirá como a documentação do seu projeto para o GitHub.

# FarmTech Solutions - Modelo de Banco de Dados

## Modelo Entidade-Relacionamento (MER)

Este modelo de banco de dados foi desenvolvido para a FarmTech Solutions, com o objetivo de implementar um sistema de monitoramento para agricultura digital. O sistema utiliza sensores para coletar dados em tempo real de plantações e auxiliar na aplicação otimizada de água e nutrientes.

### 1. Entidades e Atributos

#### Sensor
- **sensor_id** (INTEGER): Chave primária, identificador único do sensor
- **sensor_type** (INTEGER): Tipo do sensor (S1: umidade, S2: pH, S3: nutrientes)
- **model1** (VARCHAR2(50)): Modelo do sensor
- **installation_date** (VARCHAR2(20)): Data de instalação
- **location_id** (INTEGER): Referência à localização onde o sensor está instalado

#### Location (Localização)
- **location_id** (INTEGER): Chave primária, identificador único da localização
- **name** (VARCHAR2(50)): Nome da localização
- **variety** (VARCHAR2(50)): Variedade de solo ou características
- **planting_date** (DATE): Data de plantio
- **expected_harvest_date** (DATE): Data esperada para colheita
- **location_id1** (INTEGER): Possível referência hierárquica a outra localização

#### Crop (Cultura)
- **crop_id** (INTEGER): Chave primária, identificador único da cultura
- **name** (VARCHAR2(50)): Nome da cultura plantada
- **variety** (VARCHAR2(50)): Variedade da cultura
- **planting_date** (DATE): Data de plantio
- **expected_harvest_date** (DATE): Data prevista para colheita
- **location_id** (INTEGER): Referência à localização onde a cultura está plantada

#### SensoReading (Leitura do Sensor)
- **reading_id** (INTEGER): Chave primária, identificador único da leitura
- **sensor_id** (INTEGER): Referência ao sensor que realizou a leitura
- **timestamp** (DATE): Data e hora da leitura
- **reading_value** (INTEGER): Valor da leitura
- **reading_type** (VARCHAR2): Tipo de leitura (umidade, pH, fósforo, potássio)

#### IrrigationEvent (Evento de Irrigação)
- **irrigation_id** (INTEGER): Chave primária, identificador único do evento
- **location_id** (INTEGER): Referência à localização onde ocorreu a irrigação
- **timestamp** (TIMESTAMP): Data e hora do evento
- **water_amount** (NUMBER): Quantidade de água aplicada
- **duration** (INTEGER): Duração da irrigação em minutos
- **Attribute_6** (CHAR(1)): Possível indicador se foi automático (Y/N)

#### NutrientApplication (Aplicação de Nutrientes)
- **application_id** (INTEGER): Chave primária, identificador único da aplicação
- **location_id** (INTEGER): Referência à localização onde foram aplicados os nutrientes
- **timestamp** (TIMESTAMP): Data e hora da aplicação
- **nutrient_type** (VARCHAR2(20)): Tipo de nutriente aplicado
- **amount** (NUMBER): Quantidade aplicada
- **application_method** (VARCHAR2): Método de aplicação
- **is_automated** (CHAR(1)): Indica se foi automático (Y/N)

#### Sensor_with_reading (Tabela de Associação)
- **Sensor_sensor_id** (INTEGER): Parte da chave primária composta, referência ao Sensor
- **SensoReading_reading_id** (INTEGER): Parte da chave primária composta, referência à Leitura

### 2. Relacionamentos e Cardinalidades

- **Location → Sensor** (1:N): Uma localização pode ter vários sensores instalados, mas cada sensor está em apenas uma localização.

- **Location → Crop** (1:N): Uma localização pode ter várias culturas plantadas (em diferentes momentos ou áreas), mas cada registro de cultura está associado a uma localização específica.

- **Sensor → SensorReading** (1:N): Um sensor pode ter várias leituras registradas, mas cada leitura vem de um sensor específico. Este relacionamento é implementado através da tabela de associação `Sensor_with_reading`.

- **Location → IrrigationEvent** (1:N): Uma localização pode ter vários eventos de irrigação, mas cada evento de irrigação ocorre em uma localização específica.

- **Location → NutrientApplication** (1:N): Uma localização pode ter várias aplicações de nutrientes, mas cada aplicação de nutrientes ocorre em uma localização específica.

### 3. Descrição Funcional

O sistema permite:

1. **Monitoramento em Tempo Real**: Coleta e armazenamento de leituras de sensores para análise contínua das condições de solo e planta.

2. **Gerenciamento de Irrigação**: Registro e controle de eventos de irrigação, permitindo a análise de uso de água e eficiência.

3. **Gerenciamento de Nutrientes**: Registro e controle de aplicações de nutrientes, permitindo análise de uso e eficiência.

4. **Previsão e Otimização**: Com base nos dados históricos, o sistema pode prever necessidades futuras e otimizar o uso de recursos como água e nutrientes.

5. **Gerenciamento de Culturas**: Acompanhamento do ciclo de vida das culturas, desde o plantio até a colheita.

Este modelo de banco de dados suporta a implementação de um sistema de agricultura de precisão, permitindo o uso otimizado de recursos e aumento da produtividade através do monitoramento contínuo e análise de dados.

See model: 
https://github.com/leonardocamacho1983/Cap-1---Um-mapa-do-tesouro/edit/main/README.md#:~:text=04%2D15%20at-,20.29.13,-%402x.jpg
