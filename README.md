# ISO 20022 Financial Message Parser & Validator — Python SDK

[![PyPI version](https://img.shields.io/pypi/v/stanzaapi-iso20022-parser.svg)](https://pypi.org/project/stanzaapi-iso20022-parser/)
[![Python Versions](https://img.shields.io/pypi/pyversions/stanzaapi-iso20022-parser.svg)](https://pypi.org/project/stanzaapi-iso20022-parser/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> SWIFT ISO 20022 XML-to-JSON parser and compliance engine for pacs.008, camt.053, and pain.001 with sub-5ms edge latency.

Official, zero-dependency Python 3.8+ client library for **ISO 20022 Financial Message Parser & Validator**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Intended for enterprise data pipelines, backend verification, and sub-5ms edge compute.

* 🌐 **Live Web Playground:** [Test your inputs online](https://stanzaapi.com/tools/iso20022-parser)
* 📚 **API Documentation:** [View full schema on Stanza](https://stanzaapi.com/tools/iso20022-parser)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

```bash
pip install stanzaapi-iso20022-parser
```

---

## 🚀 Quickstart

```python
import os
from stanzaapi_iso20022_parser import Iso20022ParserClient

# Initialize client (api_key optional for local evaluation)
client = Iso20022ParserClient(
    api_key=os.getenv("STANZA_API_KEY")
)

# Execute deterministic validation
response = client.parse("<Document xmlns=\"urn:iso:std:iso:20022:tech:xsd:pacs.008.001.08\">...</Document>")

if response.get("success"):
    print("Verification Success:", response["data"])
else:
    print("Validation Error:", response.get("error"), response.get("code"))
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "message_type": "pacs.008.001.08",
    "settlement_amount": 150000,
    "currency": "EUR",
    "instruction_id": "INSTR-2026-0982"
  }
}
```

---

## ⚙️ Client Options

| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `api_key` | `Optional[str]` | `os.getenv("STANZA_API_KEY")` | Your [Stanza API Key](https://stanzaapi.com). Required for production quotas. |
| `base_url` | `Optional[str]` | `"https://api.stanzaapi.com/iso20022-parser"` | Public edge API base URL. |
| `timeout` | `int` | `15` | Request timeout in seconds. |


---

## 🔗 Useful Links

* [ISO 20022 Financial Message Parser & Validator Interactive Sandbox](https://stanzaapi.com/tools/iso20022-parser)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/iso20022-parser-python)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
