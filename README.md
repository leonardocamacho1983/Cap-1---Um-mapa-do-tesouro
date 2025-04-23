# 🌱 FarmTech Solutions - Modelo de Banco de Dados

Este repositório contém a modelagem relacional do sistema de monitoramento agrícola inteligente da startup **FarmTech Solutions**, voltado para otimização da irrigação e aplicação de nutrientes com base em dados coletados por sensores distribuídos em plantações.

## 📌 Objetivo

Criar uma estrutura de banco de dados relacional capaz de armazenar e analisar os dados coletados por sensores de umidade, pH e nutrientes (nitrogênio, fósforo e potássio), possibilitando:

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

- **Um Talhão**  tem **uma ou mais Zonas**. **Uma Zona** pertence a **um Talhão**.
- **Uma Zona** pode conter **nenhum ou múltiplos Sensores**. **Um Sensor** pertence a **uma Zona**.
- **Uma Zona** podeter **uma ou nenhuma Cultura**. **Uma Cultura** está plantada em **uma Zona**.
- **Um Sensor** pode ter muitas ou nenhuma **Leitura**. **Uma Leitura** pertence a **um Sensor**.

---

## 📁 Conteúdo do Repositório

- `Farmtech_diagram.png` — Imagem do diagrama (DER)
- `Farmtech_diagram.pdf` — Arquivo PDF do diagrama (DER)
- `Farmtech_diagram.pdf` — Arquivo DMD do modelo
- `README.md` — Este documento explicativo

---

## 👤 Integrantes do grupo

- [Edmilson Marciano](https://github.com/marciano64) - RM565912
- [Jayro Mazzi Junior](https://github.com/jayrom) - RM565576
- [Leonardo Camacho](leonardocamacho1983) - RM565099
- [Lucas Arcanjo](https://github.com/ArcanjoLucas00) - RM563353

---

## 🗂️ Capítulo e Fase

Fase 2 — Capítulo 1: *Um Mapa do Tesouro*

---

## ✅ Observações

- Modelo desenvolvido no Oracle SQL Developer Data Modeler
- Atenção às boas práticas de normalização e uso de chaves primárias e estrangeiras
- O modelo permite expansão futura com tabelas de aplicação de insumos, alertas e predições baseadas em dados históricos.
