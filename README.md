# Projekt Stream deck - Jakub Kučera
## Dobrý den, v tomto příspěvku Vám odevzdávám rozpracovaný projekt
### Tento projekt slouží pro ovládání hlasitosti v počítači, časem by jsem to chtěl naprogramovat pouze na ovládání různých funkcí v určitých aplikacích

## Zadání
Do 3. ročníku jsem ani nevěděl, že nějaké ESP32 existuje, nevěděl jsem o tom nic. Nicméně toto téma a myšlenka, co vše se s tímto dá dělat mě zaujala a hodně HW jsem si koupil a občas si programuji nějaké menší programy doma. Nevěděl jsemn co dělat za projekt a děkuji Vám, že jste mi pomohl vymyslet projekt, na kterém momentálně pracuji. Myšlenka projektu je taková, že se pokusím vytvořit komunikaci ESP32 a stolním PC s určitými aplikacemi jako jsou např.: Spotify(změna hlasitosti), Discord(Mute tlačítko). Celé To bude fungovat, že displej bude jako grafický prvek a pod ním bude tlačítko, s tím, že ESP32 bude číst změnu signálu na tomto tlačítku, které poté bude komunikovat s PC.
## Stav projektu 
Jelikož jsem blbec a rozbil jsem si druhý displej tak momentálně mám jenom jeden, tak pracuji pouze s tímto displejem. Momentálně se snažím vymyslet nějaký obrázek, který bude na displeji a poté se budu věnovat komunikaci ESP32 s PC. 
## Průběh práce na projektu
Ze začátku roku jsem zkouśel různé projekty napŕ.: ovládání diod pomocí tlačítek nebo přes cloud(viz kódy níže), poté jsem zkoušel programy s displejem, např.: teploměr DHT11 a na displeji se vypisovaly hodnoty z tohoto senzoru. Dále jsem zkoušel s 5 červenými diodami a 2 tlačítky udělat kód, který simuloval start 5 světel při startu motorsportových závodů, jedno tlačítko seplo postupné rozsvícení světel a druhé je vyplo, zde jsem se snažil využít interrupty, bohužel jsem se s tímto komandem toliká nenaučil a v žádném funkčním kódu ho ještě nemám. 
## Schémata
### Pro lepší zobrazení a čtení schémat jsem zvolil možnost ukázky zapojení, které jsem vytvořil na Wokwi.com. 
![image](https://github.com/Vajco06/Projekt1/assets/154622913/bda0052e-48dd-48d4-b043-1e01e8d0d1b1)

Schéma zapojení displeje, můj displej používá SCK pin


![image0 (2)](https://github.com/Vajco06/Projekt1/assets/154622913/f6ab5f72-f40c-4224-b8a0-2ee1c3b87c09) 

Zde je, jak jsem zapojil displej (Ahoj, Pepik tam je, aby se něco vypsalo :D)


![image](https://github.com/Vajco06/Projekt1/assets/154622913/ea55dc36-165a-42a3-a16a-a4719aea1156)


Zde je chéma zapojení simulace závodních světel, ten bzučák, vždy když se sepne jedna dioda, tak udělá zvuk. U diod jsou 330 Ohmové odpory, protože Červené diody fungují na 1,3V a z konektoru vychází 3,3V.

## Kódy
### Zde budou kódy ke schématům uvedeným výše a kratší popis kódu. 


#### Toto je kód na displej. V kódu se musí nadefinovat výška a šířka displeje a poté se už jenom nastavuje kurzor a co má napsat, ještě jsem se nenaučil kreslit.  

#include <Adafruit_SSD1306.h>  
#include <Adafruit_GFX.h>  
#define SCREEN_WIDTH 128   
#define SCREEN_HEIGHT 64   

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);  

void setup() {  
  display.clearDisplay();  
}  
  
void loop() {  
  display.clearDisplay();  
  display.setTextSize(1);  
  display.setTextColor(SSD1306_WHITE);  
  display.setCursor(0,0);  
  display.println("Ahoj");  
  display.setCursor(20,0);  
  display.print("Pepik");  
  display.display();  
  delay(2000);  
}  


#### Toto je kód pro simulaci závodních světel. Tento kód funguje na funkci if, když se změní signál na tlačítku tak se spustí funkce a to samé s druhým tlačítkem. U rezistrů, když se nastavuje pinMode jsem zvolil funkci INPUT_PULLUP, aby jsem nemusel zapojovat navíc rezistor na nepájivé pole.

  
void setup(){  
  pinMode(18, OUTPUT);  
  pinMode(19, OUTPUT);  
  pinMode(21, OUTPUT);  
  pinMode(22, OUTPUT);  
  pinMode(23, OUTPUT);  
  pinMode(12, INPUT_PULLUP);  
  pinMode(13, INPUT_PULLUP);  
  pinMode(5, OUTPUT);  
}  
  
void loop(){  
  if (digitalRead(12) == 0){  
    digitalWrite(19, HIGH);  
    digitalWrite(5, HIGH);  
    delay(70);  
    digitalWrite(5, LOW);  
    delay(1000);  
    digitalWrite(18, HIGH);  
    digitalWrite(5, HIGH);  
    delay(70);  
    digitalWrite(5, LOW);  
    delay(1000);  
    digitalWrite(21, HIGH);  
    digitalWrite(5, HIGH);  
    delay(70);  
    digitalWrite(5, LOW);  
    delay(1000);  
    digitalWrite(22, HIGH);  
    digitalWrite(5, HIGH);  
    delay(70);  
    digitalWrite(5, LOW);  
    delay(1000);  
    digitalWrite(23, HIGH);  
    digitalWrite(5, HIGH);  
    delay(70);  
    digitalWrite(5, LOW);  
    delay(1000);  
  }  
  if(digitalRead(13) == 0){  
    digitalWrite(19, LOW);  
    digitalWrite(18, LOW);  
    digitalWrite(21, LOW);  
    digitalWrite(22, LOW);  
    digitalWrite(23, LOW);  
    digitalWrite(5, HIGH);  
    delay(90);  
    digitalWrite(5, LOW);  
  }  
}  

## Spolupracovníci
Celkově s pochopení ESP32 a HW k němu mi pomohl Míra Pich, Radim Krb a Dominik Bašek, konkrétně s Mírou a Dominikem jsem se snažil při hodinách pochopit zapojení displeje a Radim mi ze začátku roku vysvětloval jak funguje a jak napragomovat ESP32. Dále jsem ho používal ChatGPT, kde jsem si nechal vypsat kód, který jsem někdy poupravil, někdy nechal a podle toho jsem se učil. Poté jsem hodně čerpal ze stránek Arduino, kde jsem hlavně vyhledával funkce a použití různých komandů. 
## Zdroje
https://chat.openai.com  
https://www.arduino.cc     
https://wokwi.com 
