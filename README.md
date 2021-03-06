FCMSimple
===
A PHP class to send messages to devices registered through Firebase Cloud Messaging (FCM).

- Adapted from the code available at [GCM-PHP-Server-Push-Message](https://github.com/mattg888/GCM-PHP-Server-Push-Message) with some modifications to work with FCM instead of GCM.
- Add new feature `getUpdatedTokens`.


Usage
---
##### Installation:
Run the following command in your project-root directory
```
$ composer require coder966/fcm-simple
```

##### PHP-Server:
```php
require 'vendor/autoload.php'; // Load composer dependencies

$fcm = new FCMSimple($serverKey);
$fcm->setTokens($tokens);
$messageData = array("key1"=>"value1", "key2"=>"value2" ...);
$response = $fcm->send($messageData);
$updatedTokens = $fcm->getUpdatedTokens();

// $serverKey      Your FCM server key
// $tokens         An array of registered device tokens
// $message        The mesasge you want to push out
// $updatedTokens  An Array of updated registered device tokens

// You should then assign $updatedTokens to $tokens
```

##### Android-Client:
In the service that extends `FirebaseMessagingService`, in method `onMessageReceived` use:
```java
Map<String, String> msg = remoteMessage.getData();
```


License
---
```
Copyright 2016 Khalid Alharisi

    Licensed under the GNU General Public License v3.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       https://www.gnu.org/licenses/gpl-3.0.txt

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
```
