# 2025 11   MQ DIA Agentic architecture (1)

## Slide 1

![Slide 1](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_1.png>)

# MQ DIA – ARCHITECTURE FOR AGENTIC AI

---

*Lilly*

## Slide 2

![Slide 2](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_2.png>)

# Agents and agency

*[Image: Two stylized human head silhouettes in profile facing each other against a dark blue background. Both heads contain circuit board patterns. Between them is an upward-pointing arrow and connected geometric shapes, suggesting data flow and AI connectivity.]*

> Agency is the capacity for AI systems to understand context, make independent decisions, and take autonomous actions to achieve goals, much like human intelligence, but operating at machine speed and scale.
>
> — Brian Lewis, Eli Lilly - Technology Breakthrough Forum

GenAI represents a technological breakthrough that provides support for provides the mechanism for true agency.

- Context-aware generation, multi-modal understanding, dynamic planning
- Enables systems to perceive, reason, and create, laying the groundwork for agentic behavior.

## Slide 3

![Slide 3](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_3.png>)

# MQ-DIA Framework for Agentic AI

## Architecture Diagram Description

The diagram illustrates a multi-layer agentic AI framework flowing left to right, with a platform layer at the bottom spanning all layers.

---

### Layers (Left to Right)

#### Application Layer
Contains four black-background boxes stacked vertically:
- **Application A**
- **Application B**
- **Application C**
- **[...]**

*Bidirectional arrows connect the Application layer to the Planning layer.*

---

#### Planning Layer
Contains four green-background boxes stacked vertically:
- **Supervisor (App A)**
- **Supervisor (App B)**
- **Supervisor (App C)**
- **Supervisor (...)**

*Bidirectional arrows connect the Planning layer to the Agent layer.*

---

#### Agent Layer
Contains three blue-background boxes stacked vertically:
- **Retrieval agent (unstructured data)**
- **Retrieval agent (structured data)**
- **Executor agent**

*Bidirectional arrows connect the Agent layer to the Tools layer and Data layer.*

---

#### Tools Layer
Contains four yellow-background boxes in a 2x2 grid:
- **Tool A** (ex: communicate with system X via API)
- **Tool B** (ex: launch anomaly detection algorithm)
- **Tool C** (ex: send notification/alert on given channel)
- **Tool D (...)**

*Bidirectional arrows connect the Tools layer to the Data layer.*

---

#### Data Layer
Contains four data source items stacked vertically:
- **GMDF** (cylinder/database icon)
- **Sensor data** (cylinder/database icon)
- **API** (box icon)
- **Text/PDF/Word/Excel documents** (document stack icon)

---

### Platform Layer (Bottom, spanning all layers)
Contains five beige/tan-background boxes in a horizontal row:
- **Cortex**
- **Databricks**
- **Science Engine**
- **Azure Open AI**
- **LLM's (through Cortex)**

---

*Company Confidential © 2025 Eli Lilly and Company — Page 3*

## Slide 4

![Slide 4](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_4.png>)

# The AMIGO use case

## Architecture Diagram Description

The diagram shows a layered architecture flowing left to right, with five vertical layers separated by labeled dividers:

---

### Layer 1: Application Layer
- **AMIGO** (black box)

---

### Layer 2: Planning Layer
- **Supervisor agent** (green box)

---

### Layer 3: Agent Layer
Seven agents listed vertically (all in blue boxes):
- **RAG agent (SOP, Technical Manuals, Specifications)**
- **RAG agent (Shift handovers)**
- **RAG agent (GMARS workorder logs)**
- **RAG agent (Alarm rationalization)**
- **Retrieval agent (Batches, alarms, stoppages)**
- **Retrieval agent (GMARS spare parts and workorders)**
- **Executor agent (Intervention recommendation)**

---

### Layer 4: Tools Layer
Two tools listed (yellow boxes), aligned with corresponding agents:
- **Tool (Invokes Databricks Genie API)** — aligned with Retrieval agent (Batches, alarms, stoppages)
- **Tool (Calculates intervention recommendation)** — aligned with Executor agent (Intervention recommendation)

---

### Layer 5: Data Layer
Data sources listed vertically (gray document/database icons):
- **PDF documents from Veeva QDocs**
- **PDF documents generated from GMARS WO logs**
- **PDF documents generated from OneNote**
- **Databricks Genie API's**
- **GMDF** ← connected to → **Real time source data (through GMDF LHF)**
- **Sensor data (through Seeq)**

---

*Company Confidential © 2025 Eli Lilly and Company — Page 4*

## Slide 5

![Slide 5](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_5.png>)

# The LIDA use case

## Architecture Diagram — Layered Architecture (left to right)

The diagram shows a horizontal layered architecture with 5 layers separated by vertical dividing lines, flowing left to right:

---

### Application Layer
- **LIDA** (black box)

---

### Planning Layer
- **Supervisor agent** (green box)

---

### Agent Layer
Three agents stacked vertically:
- **Info extraction agent** (blue box)
- **Info verification agent** (blue box)
- **SAP verification agent** (blue box)

---

### Tools Layer
- **Tool (extracts info from SAP using API)** (yellow box)

---

### Data Layer
Two data sources stacked vertically:
- **Multipage PDF document** (stacked document/page icon)
- **SAP** (cylinder/database icon)

---

*Company Confidential © 2025 Eli Lilly and Company — Page 5*