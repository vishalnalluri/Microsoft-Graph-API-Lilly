# 2025 11   MQ DIA Agentic architecture (1)

## Slide 1

![Slide 1](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_1.png>)

```markdown
# MQ DIA – ARCHITECTURE FOR AGENTIC AI

_Lilly logo in the bottom left corner._
```

## Slide 2

![Slide 2](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_2.png>)

```markdown
# Agents and Agency

![Silhouette of two human faces with circuit-like designs connecting them, and arrows pointing up, symbolizing connections and agency.]

Agency is the capacity for AI systems to understand context, make independent decisions, and take autonomous actions to achieve goals, much like human intelligence, but operating at machine speed and scale.

*Brian Lewis, Eli Lilly - Technology Breakthrough Forum*

---

GenAI represents a technological breakthrough that provides support for the mechanism for true agency.  
- Context-aware generation, multi-modal understanding, dynamic planning  
- Enables systems to perceive, reason, and create, laying the groundwork for agentic behavior.  

---

*Company Confidential © 2025 Eli Lilly and Company*
```

## Slide 3

![Slide 3](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_3.png>)

```markdown
# MQ-DIA Framework for Agentic AI

---

## Layers:

### Application layer:
- **Application A**
- **Application B**
- **Application C**
- […]

---

### Planning layer:
- **Supervisor (App A)**
- **Supervisor (App B)**
- **Supervisor (App C)**
- **Supervisor (…)**

---

### Agent layer:
- **Retrieval agent (unstructured data)**
- **Retrieval agent (structured data)**
- **Executor agent**

---

### Tools layer:
- **Tool A** (e.g., communicate with system X via API)
- **Tool B** (e.g., launch anomaly detection algorithm)
- **Tool C** (e.g., send notification/alert on given channel)
- **Tool D (…)*

---

### Data layer:
- **GMDF** (cylinder icon)
- **Sensor data** (rectangular box)
- **API** (rectangular box)
- **Text/PDF/Word/Excel documents** (stacked paper icon)

---

### Platform layer:
- **Cortex**
- **Databricks**
- **Science Engine**
- **Azure Open AI**
- **LLM's (through Cortex)**

---

*Company Confidential © 2025 Eli Lilly and Company*
```

## Slide 4

![Slide 4](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_4.png>)

```markdown
# The AMIGO use case

## Application layer
- **AMIGO** (Black box)

## Planning layer
- **Supervisor agent** (Green box)

## Agent layer
- **RAG agent (SOP, Technical Manuals, Specifications)** (Blue box)
- **RAG agent (Shift handovers)** (Blue box)
- **RAG agent (GMARS workorder logs)** (Blue box)
- **RAG agent (Alarm rationalization)** (Blue box)
- **Retrieval agent (Batches, alarms, stoppages)** (Blue box)
- **Retrieval agent (GMARS spare parts and workorders)** (Blue box)
- **Executor agent (Intervention recommendation)** (Blue box)

## Tools layer
- **Tool (Invokes Databricks Genie API)** (Yellow box)
- **Tool (Calculates intervention recommendation)** (Yellow box)

## Data layer
- PDF documents from Veeva QDocs (Stack of document icons)
- PDF documents generated from GMARS WO logs (Stack of document icons)
- PDF documents generated from OneNote (Stack of document icons)
- **Databricks Genie API's** (Cylinder)
- **GMDF** (Cylinder)
- **Real time source data (through GMDF LHF)** (Cylinder)
- **Sensor data (through Seeq)** (Cylinder)
```

## Slide 5

![Slide 5](<images/2025 11 - MQ DIA Agentic architecture (1)/slide_5.png>)

```markdown
# The LIDA use case

| Application layer | Planning layer    | Agent layer                             | Tools layer                              | Data layer                    |
|-------------------|-------------------|-----------------------------------------|------------------------------------------|-------------------------------|
| **LIDA**          | **Supervisor agent** | **Info extraction agent**               | **Tool (extracts info from SAP using API)** | **Multipage PDF document**   |
|                   |                   | **Info verification agent**             |                                          | **SAP**                       |
|                   |                   | **SAP verification agent**              |                                          |                               |

### Diagram Description:
- The diagram is structured with five vertical columns, each representing a distinct layer:
  1. **Application layer:** Contains a single black box labeled "LIDA".
  2. **Planning layer:** Contains a green box labeled "Supervisor agent".
  3. **Agent layer:** Contains three blue boxes stacked vertically, labeled:
     - "Info extraction agent"
     - "Info verification agent"
     - "SAP verification agent"
  4. **Tools layer:** Contains a yellow box labeled "Tool (extracts info from SAP using API)".
  5. **Data layer:** Includes:
     - A stack of gray sheets labeled "Multipage PDF document".
     - A gray cylinder labeled "SAP".
```