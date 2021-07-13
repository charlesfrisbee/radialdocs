
# Radial Simple Support API

Radial is currently developing a REST API to simplify the process of engineering simply supported beams. This is an extension of a tried and tested Excel workbook developed by Radial/Cantilever Connections.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install foobar
```

The API exposes a single POST endpoint at:

## Headers
The API is protected by an API key which must be included in the request header as follows:

x-api-key: "YOUR_API_KEY_HERE"

Please get in touch with Radial to obtain a valid key.

## Body
The API expects a request body to be a JSON object containing:
1. Load data
2. Beam span
3. Maximum deflection limit

### Load data
The load data is an array of JSON objects representing the unfactored loads applied to the beam. These loads may be either:

1. Point loads
2. Uniformly Distributed Loads (UDLs)
3. Partial UDLs (UDLs acting on part of the beam)

The type of load applied to the beam is communicated through the "loadPattern" property in the JSON load object. Each load object must also have a "loadCase" property (either DL, LL or WL - Dead, Live, Wind respectively) and a "loadAmount" property which is given in kN for Point loads and kN/m for the UDLs.

Shown below is an example request body adhering to the above:

```yaml
{
  "loads": [
    {
      "loadPattern": "Point",
      "loadCase": "DL",
      "loadAmount": 10,
      "loadPosition": 0.25
    }, 
    {
      "loadPattern": "UDL",
      "loadCase": "DL",
      "loadAmount": 10
    },
    {
      "loadPattern": "PartialUDL",
      "loadCase": "LL",
      "loadAmount": 4,
      "loadStart": 0.5,
      "loadEnd": 0.8
    }
  ],
  "span": 5,
  "deflectionLimit": 10
}
```

In other words, the request body must contain an array of JSON objects representing the loads

## Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## TODOS

- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item

## License
[MIT](https://choosealicense.com/licenses/mit/)
