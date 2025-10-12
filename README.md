---
title: Email Classifier API
emoji: ✉️
colorFrom: blue
colorTo: indigo
sdk: docker
app_port: 8000
---

# Email Classification API

Automatically classifies support emails and masks PII.

## API Usage
```python
import requests

response = requests.post(
    "https://yourusername-your-space.hf.space/classify",
    json={"input_email_body": "My card is 4111-1111-1111-1111. Need help!"}
)
print(response.json())
```

## Configuration
- **Model**: DistilBERT fine-tuned on support emails
- **PII Masking**: Regex + spaCy NER
- **Categories**: Incident, Request, Change, Problem