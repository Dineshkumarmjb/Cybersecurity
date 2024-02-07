# Cybersecurity Model for Entity Recognition

## Overview

This repository contains a Python implementation of a cybersecurity entity recognition model using the SecureBERT-NER (Named Entity Recognition) model from CyberPeace Institute. The model is designed to identify various entities related to cybersecurity, such as Authentication Identities, Security Teams, Tools, Time, and Attack indicators within a given text.

## Getting Started

### Prerequisites

Before running the code, ensure that you have the required Python packages installed. You can install them using the following command:

```bash
pip install transformers
```

### Usage

1. Import the necessary libraries:

```python
from transformers import pipeline
```

2. Initialize the pipeline with the pre-trained SecureBERT-NER model:

```python
nlp = pipeline('ner', model='CyberPeace-Institute/SecureBERT-NER')
```

3. Provide a sample security advisory text:

```python
text = """
Cyberattacks are rampant across all industries. A report by Cybersecurity Ventures states that by the end of December 2031, a ransomware attack is expected to target a business every 2 seconds. From WannaCry in 2017 to REvil in 2021, IT enterprises are under immense pressure. With new malware variants discovered each day, businesses need to make sure their endpoints are secure by employing the right security controls
In 2022 alone, the total number of global ransomware reports increased by 80% year-over-year, according to a report by ZScaler. If your business hasn't equipped itself with security controls that can work proactively and prevent evolving cyberattacks, it's high time to enhance your enterprise cybersecurity by downloading Endpoint Central, ManageEngine's UEM solution.
"""
```

4. Use the pipeline to extract entities from the text:

```python
entities = nlp(text)
```

5. Filter the entities based on their types:

```python
Identities = [entity for entity in entities if entity['entity'] == 'B-IDTY' or entity['entity'] == 'I-IDTY']
Security_team = [entity for entity in entities if entity['entity'] == 'I-SECTEAM' or entity['entity'] == 'B-SECTEAM']
Tool = [entity for entity in entities if entity['entity'] == 'I-TOOL' or entity['entity'] == 'B-TOOL']
Time = [entity for entity in entities if entity['entity'] == 'I-TIME' or entity['entity'] == 'B-TIME']
Attack = [entity for entity in entities if entity['entity'] == 'I-ACT' or entity['entity'] == 'B-ACT']
```

6. Print the extracted entities:

```python
# Print the Identities
for idty in Identities:
    print(f"Authentication Identity: {idty['word']}")

# Print Security Teams
for st in Security_team:
    print(f"Security Team: {st['word']}")

# Print Tools
for tool in Tool:
    print(f"Tool: {tool['word']}")

# Print Time
for time in Time:
    print(f"Time: {time['word']}")

# Print Attacks
for attack in Attack:
    print(f"Attack: {attack['word']}")
```

## Acknowledgments

- CyberPeace Institute for providing the SecureBERT-NER model.
