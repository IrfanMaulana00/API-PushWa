# API-PushWa
PushWa - API Whatsapp Gateway Indonesia
<a href="https://www.postman.com/dark-robot-205579/workspace/api-whatsapp/collection/11510019-ad5d2f03-25c1-4251-8558-b7f8d2d71a5d?action=share&creator=11510019" target="_NEW">Open Postman Link</a><br>
Register on <a href="https://PushWa.com" target="_NEW">PushWa.com</a>

## Start Device

### Request
Example PHP Code :
```php
<?php

$token = "YOUR TOKEN";

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/startDevice',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => json_encode([
    'token' => $token
  ]),
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

### Response
#### Success
```json
{
    "status": true,
    "qr": "2@f9VV1SVgFILtD5R+EgEwndA6Vrty3xRtpjb8IIEZRfKGGlqrLY5DVWfe66nqQRfx1SFuXpVQGmFFqg==,gHy/2y6O0ERYPIjaWsmRPuUPoySnANPdlozXJ5UPLzc=,KR4p9trn1iELmQ1ClMZ2VhfEi1cz/wpCQaL0peDU8QQ=,6819Z6Y32I8+DGKiePhP6/GDzXu9t0fXbwnSZKfKKZY="
}
```

#### Device Connected
```json
{
    "status": true,
    "message": "connected"
}
```

#### Failed
```json
{
    "status": false,
    "message": "Token not valid."
}
```

## Send Message

### Message
Example PHP Code :
```php
<?php

$token = "YOUR TOKEN";

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/kirimPesan',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => json_encode([
    'token' => $token,
    'target' => "628123456789",
    'type' => "text",
    'delay' => "1",
    'message' => "Hello Word\nHallo dunia"
  ]),
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

### Attachment
You need to send the attachment link in the url parameter.

Example PHP Code :
```php
<?php

$token = "YOUR TOKEN";

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/kirimPesan',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => json_encode([
    'token' => $token,
    'target' => "628123456789",
    'type' => "image",
    'delay' => "1",
    'message' => "Hello Word\nHallo dunia",
    "url" : "https://www.shutterstock.com/image-photo/red-apple-isolated-on-white-600w-1727544364.jpg" 
  ]),
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

### Multi Target
you need to input several target numbers, combine them with a comma separator (,)

Example PHP Code :
```php
<?php

$token = "YOUR TOKEN";

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/kirimPesan',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => json_encode([
    'token' => $token,
    'target' => "628123456789,62889237498",
    'type' => "text",
    'delay' => "1",
    'message' => "Hello Word\nHallo dunia"
  ]),
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

### Using Variable
We support the use of variables, you need to add the variable to the target parameter, with the | separator for each variable and call it in the message with {var1} {var} etc

Example PHP Code :
```php
<?php

$token = "YOUR TOKEN";

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/kirimPesan',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => json_encode([
    'token' => $token,
    'target' => "628123456|Robert|Beijing,628897923|David|Indonesia", 
    'type' => "text",
    'delay' => "1",
    'message' => "Hello {var1} from {var2}"
  ]),
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

## Response Send Message
```json
{
    "status": true,
    "message": "Pesan akan segera diproses.",
    "idMsg": [
        151
    ]
}
```

## Check Status Message
This API is used to check message delivery status.

### Request
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://dash.pushwa.com/api/statusMessage',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "token": "KldvHyxQ1m8kJY3hLuVGpBUnKJSDHKF3H2HK2",
    "idMsg" : "148,149,150"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

### Response
```php
{
    "status": true,
    "message": "OK",
    "data": [
        {
            "id": "148",
            "status": "success"
        },
        {
            "id": "149",
            "status": "success"
        },
        {
            "id": "150",
            "status": "success"
        }
    ]
}
```
