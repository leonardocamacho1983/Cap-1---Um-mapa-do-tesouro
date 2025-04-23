# 🌱 FarmTech Solutions - Modelo de Banco de Dados

Este repositório contém a modelagem relacional do sistema de monitoramento agrícola inteligente da startup **FarmTech Solutions**, voltado para otimização da irrigação e aplicação de nutrientes com base em dados coletados por sensores distribuídos em plantações.

## 📌 Objetivo

Criar uma estrutura de banco de dados relacional capaz de armazenar e analisar os dados coletados por sensores de umidade, pH e nutrientes (fósforo e potássio), possibilitando:

- Visualização e histórico de leituras de sensores
- Aplicação eficiente de água e insumos
- Monitoramento contínuo por zonas e talhões
- Otimização da produção com base em dados históricos

---

## 🧩 Entidades do Modelo

### 1. `Talhão`
Representa uma subdivisão da fazenda.

| Atributo     | Tipo     | Descrição                       |
|--------------|----------|---------------------------------|
| FIELD_ID     | Integer  | Identificador único do talhão   |
| FIELD_Nome   | VARCHAR  | Nome do talhão                  |
| FIELD_X      | Integer  | Coordenada X no mapa            |
| FIELD_Y      | Integer  | Coordenada Y no mapa            |

---

### 2. `Zona`
Zonas dentro de um talhão onde sensores são instalados.

| Atributo     | Tipo     | Descrição                        |
|--------------|----------|----------------------------------|
| PLOT_ID      | Integer  | ID único da zona                 |
| FIELD_ID     | Integer  | FK para Talhão                   |
| PLOT_Name    | VARCHAR  | Nome ou código da zona           |
| PLOT_X       | Integer  | Coordenada X da zona             |
| PLOT_Y       | Integer  | Coordenada Y da zona             |

---

### 3. `Cultura`
Cultura agrícola plantada em uma zona.

| Atributo     | Tipo     | Descrição                          |
|--------------|----------|------------------------------------|
| CROP_ID      | Integer  | ID único da cultura                |
| PLOT_ID      | Integer  | FK para Zona                       |
| CROP_Name    | VARCHAR  | Nome da cultura (ex: milho, soja)  |

---

### 4. `Sensor`
Dispositivos instalados para coleta de dados ambientais.

| Atributo      | Tipo     | Descrição                                  |
|---------------|----------|---------------------------------------------|
| SENSOR_ID     | Integer  | ID único do sensor                          |
| PLOT_ID       | Integer  | FK para Zona                                |
| SENSOR_name   | VARCHAR  | Nome ou código identificador do sensor      |
| SENSOR_Type   | VARCHAR  | Tipo: umidade, pH ou NPK                    |

---

### 5. `Leitura`
Registros de leitura feitas pelos sensores.

| Atributo         | Tipo     | Descrição                                |
|------------------|----------|------------------------------------------|
| READING_PK       | Integer  | ID da leitura                            |
| SENSOR_ID        | Integer  | FK para o sensor                         |
| READING_Datahora | Datetime | Data e hora da leitura                   |
| READING_Value    | Float    | Valor registrado (ex: pH = 6.2)          |

---

## 🔗 Relacionamentos

- **Um Talhão** pode ter **várias Zonas** (1:N)
- **Uma Zona** pode conter **múltiplos Sensores e Culturas** (1:N)
- **Um Sensor** pode ter **várias Leituras** (1:N)

---

## 📁 Conteúdo do Repositório

- `farmtech_model.sql` — Script SQL gerado com os comandos de criação das tabelas
- `farmtech_model.xml` — Arquivo do modelo exportado em XML
- `farmtech_model.png` — Imagem do DER
- `README.md` — Este documento explicativo

---

## 👤 Integrantes do grupo

- João Santos - RM123456
- Ana Oliveira - RM654321
- Bruno Silva - RM112233
- Camila Ferreira - RM998877
- Leonardo Camacho - RM765432

---

## 🗂️ Capítulo e Fase

Fase 2 — Capítulo 1: *Um Mapa do Tesouro*

---

## ✅ Observações

- Modelo desenvolvido no Oracle SQL Developer Data Modeler
- Atenção às boas práticas de normalização e uso de chaves primárias e estrangeiras
- O modelo permite expansão futura com tabelas de aplicação de insumos, alertas e predições baseadas em dados históricos.
