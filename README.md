# API-PushWa
API PushWa Whatsapp Gateway
<a href="https://www.postman.com/dark-robot-205579/workspace/api-whatsapp/collection/11510019-ad5d2f03-25c1-4251-8558-b7f8d2d71a5d?action=share&creator=11510019" target="_NEW">Open Postman Link</a><br>

## Send Message
Example PHP Code :
```
<?php

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
  CURLOPT_POSTFIELDS =>'{
    "token": "TOKEN",
    "target" : "62812xxxx", 
    "type" : "text", 
    "delay" : "1",
    "message" : "Hello World"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

## Send Attachment
You need to send the attachment link in the url parameter.

Example PHP Code :
```
<?php

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
  CURLOPT_POSTFIELDS =>'{
    "token": "TOKEN",
    "target" : "62812xxxx", 
    "type" : "text", 
    "delay" : "1",
    "message" : "Hello World",
    "url" : "https://www.shutterstock.com/image-photo/red-apple-isolated-on-white-600w-1727544364.jpg" 
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

## Send Message (Multi Target)
you need to input several target numbers, combine them with a comma separator (,)

Example PHP Code :
```
<?php

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
  CURLOPT_POSTFIELDS =>'{
    "token": "TOKEN",
    "target" : "628123456,628897923", 
    "type" : "text", 
    "delay" : "1",
    "message" : "Hello World"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```

## Send Message (With Variable)
We support the use of variables, you need to add the variable to the target parameter, with the | separator for each variable and call it in the message with {var1} {var} etc

Example PHP Code :
```
<?php

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
  CURLOPT_POSTFIELDS =>'{
    "token": "TOKEN",
    "target" : "628123456|Robert|Beijing,628897923|David|Indonesia", 
    "type" : "text", 
    "delay" : "1",
    "message" : "Hello {var1} from {var2}"
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json'
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```