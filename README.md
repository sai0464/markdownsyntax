 # Telegram based Home automation 
 ## components
 ### circuit diagram
 #### analysis
 ##### output observation 
 ###### conclusion
**sample text**

__sample__
## Italic text
*sample text*
 
_sample text_
## Bold & Italic
**_sample text_**

__*sampe text*__
## Blockquote
>   dhjgfdhhfdkssdjkhfhgfjgjgfhsgjgvhdhfgdsgjjhgfgds;hf;sdsgfgjhdsgfgfgh
## Nested Blockquote
> dshfjdhjfdjfjdjfj
>> dhfgg dhfg h kddhjf dcgx fhjcg
>>> hfhdhgdhjcdfjjjdfkgfhghsshlsdaghhgdgsfhhghghhfg
## Ordered List
1. ece
2. mech
3. cse
    1. cseA
    2. CSEB
4. civil
5. EEE
## Unorderd List
- ece
    * EceA
    * ECEB
- EEE
    * EEEA
    * EEEB
## code
```
 def fun():
    printf("welcome to github training");  
```
## function calling
  `
  fun()    
 `
 ## arcode   
 ```
 /*******************************************************************
 *  An example of bot that receives commands and turns on and off  *
 *  an LED.                                                        *
 *                                                                 *
 *  written by Giacarlo Bacchio (Gianbacchio on Github)            *
 *  adapted by Brian Lough                                         *
 *******************************************************************/
#include <ESP8266WiFi.h>
#include <WiFiClientSecure.h>
#include <UniversalTelegramBot.h>

// Initialize Wifi connection to the router
char ssid[] = "sai Jayanth";     // your network SSID (name)
char password[] = "12345678"; // your network key

// Initialize Telegram BOT
#define BOTtoken "1079855748:AAHQi9QfNXBUWCoUIdMUVdyAYif_C2AwW70"  // your Bot Token (Get from Botfather)

WiFiClientSecure client;
UniversalTelegramBot bot(BOTtoken, client);

int Bot_mtbs = 1000; //mean time between scan messages
long Bot_lasttime;   //last time messages' scan has been done
bool Start = false;

const int ledPin = D0;
int ledStatus = 0;

void handleNewMessages(int numNewMessages) {
  Serial.println("handleNewMessages");
  Serial.println(String(numNewMessages));

  for (int i=0; i<numNewMessages; i++) {
    String chat_id = String(bot.messages[i].chat_id);
    String text = bot.messages[i].text;

    String from_name = bot.messages[i].from_name;
    if (from_name == "") from_name = "Guest";

    if (text == "/ledon") {
      digitalWrite(ledPin, HIGH);   // turn the LED on (HIGH is the voltage level)
      ledStatus = 1;
      bot.sendMessage(chat_id, "Led is ON", "");
    }

    if (text == "/ledoff") {
      ledStatus = 0;
      digitalWrite(ledPin, LOW);    // turn the LED off (LOW is the voltage level)
      bot.sendMessage(chat_id, "Led is OFF", "");
    }

    if (text == "/status") {
      if(ledStatus){
        bot.sendMessage(chat_id, "Led is ON", "");
      } else {
        bot.sendMessage(chat_id, "Led is OFF", "");
      }
    }

    if (text == "/start") {
      String welcome = "Welcome to Universal Arduino Telegram Bot library, " + from_name + ".\n";
      welcome += "This is Flash Led Bot example.\n\n";
      welcome += "/ledon : to switch the Led ON\n";
      welcome += "/ledoff : to switch the Led OFF\n";
      welcome += "/status : Returns current status of LED\n";
      bot.sendMessage(chat_id, welcome, "Markdown");
    }
  }
}


void setup() {
  Serial.begin(115200);

  // Set WiFi to station mode and disconnect from an AP if it was Previously
  // connected
  WiFi.mode(WIFI_STA);
  WiFi.disconnect();
  delay(100);

  // attempt to connect to Wifi network:
  Serial.print("Connecting Wifi: ");
  Serial.println(ssid);
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(500);
  }

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.print("IP address: ");
  Serial.println(WiFi.localIP());

  pinMode(ledPin, OUTPUT); // initialize digital ledPin as an output.
  delay(10);
  digitalWrite(ledPin, LOW); // initialize pin as off
}

void loop() {
  if (millis() > Bot_lasttime + Bot_mtbs)  {
    int numNewMessages = bot.getUpdates(bot.last_message_received + 1);

    while(numNewMessages) {
      Serial.println("got response");
      handleNewMessages(numNewMessages);
      numNewMessages = bot.getUpdates(bot.last_message_received + 1);
    }

    Bot_lasttime = millis();
  }
}
```
## Links
[google](https://www.google.com)

## add gmaillink
[gmail](https://mail.google.com/mail)

## add college website
[KITS](https://collegedunia.com/college/14034-krishna-chaitanya-institute-of-technology-and-sciences-kits-prakasam)
## git commands
- git init
- git status
- git branch
- git add filename
- git remote
- git remote -v 
- git clone "url"
- git remote add remotename "repolink"
- git log
- git log --oneline
- git revet filename
- git reset filename
- git rm filename
- git config user.name "username"
- git config user.mail "usermail"
- git commit -m "message"
 - git push remotename branchname
- git pull remotename branchname
## inserting image
![myimage](https://github.com/sai0464/markdownsyntax/blob/master/photo1.jpg)
## Inserting Videos
[![CHECK](https://img.youtube.com/vi/glgN50DmvYE/0.jpg)](https://www.youtube.com/watch?v=glgN50DmvYE)
[![vantalakka](https://img.youtube.com/vi/WNiPgBumlxk/0.jpg)](https://www.youtube.com/watch?v=WNiPgBumlxk)
