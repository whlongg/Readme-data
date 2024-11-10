# ENDPOINT ElderCare Project
## Convert Speech To Text
### CURL:
```curl
curl -X 'POST' \
  'http://localhost:8000/api/speech-to-text/?language=vi-VN' \
  -H 'accept: application/json' \
  -H 'Content-Type: multipart/form-data' \
  -F 'file=@audio.wav;type=audio/wav'
```
### query Parameters:
- language(string): any (Default: "vi-VN")
### Request Body schema: 
- file (required): audio/wav (File)
### Response:
- 200: ```{"text": string}```
- 422: 
```json
  "detail": [
    {
      "loc": [
        "string",
        0
      ],
      "msg": "string",
      "type": "string"
    }
  ]
```
## Convert Text To Speech
### CURL:
```
curl -X 'POST' \
  'http://localhost:8000/api/text-to-speech/' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "text": "string"
}'
```
### Request Body schema: 
- text (*required*): string (Text)
- model: string (Model) Default: "tts-1"
- voice: string (Voice) Default: "alloy"
- speed: number (Speed) Default: 1

### Response:
- 200: audio/wav (File)
- 422: 
```json
  "detail": [
    {
      "loc": [
        "string",
        0
      ],
      "msg": "string",
      "type": "string"
    }
  ]
```

