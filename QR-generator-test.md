# QR-generator

Make sure you have read the [README.md](https://github.com/Superformula/mobile-test/blob/master/README.md) first.

Be sure to read **all** of this document carefully, and follow the guidelines within.

## Context

- A client needs to display a QR code in their App.
- The App is a typical membership App, which can be used to access features of one's membership.
- The QR code can be used to identify one's membership or feature.

## Requirements

### Tasks

1.  Build a simple API server that provides an endpoint which generates a random seed used to create QR code.
2.  Build a simple App that can call the seed endpoint and generate a QR code based on the seed.

### UI

Here's a quick mock-up of how it could look like (simple like Material Design!):
![UI Example](https://user-images.githubusercontent.com/10452/43813647-6e6ccbf4-9a7b-11e8-84f7-3b17ad5b2e30.png)

### API

(in Open API 3.0 format)

```yaml
paths:
  /seed:
    get:
      description: Get a seed that can be used to generate a QR code
      responses:
        '200':
          description: seed generated
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Seed'
components:
  schemas:
    Seed:
      type: object
      properties:
        seed:
          type: string
          example: d43397d129c3de9e4b6c3974c1c16d1f
        expires_at:
          type: dateTime
          description: ISO date-time
          example: '1979-11-12T13:10:42.24Z'
```

### Tech stack

- API
  - Use anything for the backend. We generally use Node.js, so this is prefered but not required.
- Android
  - Use Kotlin
- iOS
  - Use Swift

### Bonus

- Write clear **documentation** on how it's designed and how to execute the code.
- Provide proper unit tests.
- Write concise and clear commit messages.

### Advanced requirements

These may be used for additional challenges. You can freely skip these if you are not asked to do them; feel free to try them out if you're up for it.

- Provide an auto-refresh strategy, for example with the `expires_at` value.
- Provide an offline QR code access strategy, for example with a cache.
- Build a "Scan" feature that can demonstrate how it works (see the mock) and how it could be validated with another endpoint.
