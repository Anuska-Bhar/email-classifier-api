# Email Classification API

Automatically classifies support emails and masks PII.

## How It Works
Input Email → PII Detection → Masking → TF-IDF → Logistic Regression → JSON Response

## Quick Start
```python
import requests

response = requests.post(
    "https://yourusername-your-space.hf.space/classify",
    json={"input_email_body": "My card is 4111-1111-1111-1111. Need help!"}
)
print(response.json())
```

## Example Response

```json
{
  "input_email_body": "My name is John Doe. Card: 4111-1111-1111-1111",
  "masked_email": "My name is [full_name]. Card: [credit_debit_no]",
  "list_of_masked_entities": [
    { "entity": "John Doe", "classification": "full_name", "position": [11, 19] }
  ],
  "category_of_the_email": "Request"
}
```

## Configuration
- **Model**: DistilBERT fine-tuned on support emails
- **PII Masking**: Regex + spaCy NER
- **Categories**: Incident, Request, Change, Problem
