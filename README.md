# Projekt Stream deck - Jakub Kučera
## Dobrý den, v tomto příspěvku Vám odevzdávám rozpracovaný projekt
### Tento projekt slouží pro ovládání hlasitosti v počítači, časem by jsem to chtěl naprogramovat pouze na ovládání různých funkcí v určitých aplikacích

## Zadání
Do 3. ročníku jsem ani nevěděl, že nějaké ESP32 existuje, nevěděl jsem o tom nic. Nicméně toto téma a myšlenka, co vše se s tímto dá dělat mě zaujala a hodně HW jsem si koupil a občas si programuji nějaké menší programy doma. Nevěděl jsemn co dělat za projekt a děkuji Vám, že jste mi pomohl vymyslet projekt, na kterém momentálně pracuji. Myšlenka projektu je taková, že se pokusím vytvořit komunikaci s ESP32 a stolním PC s určitými aplikacemi jako jsou např.: Spotify(změna hlasitosti), Discord(Mute tlačítko). Celé To bude fungovat, že displej bude jako grafický prvek a pod ním bude tlačítko, s tím, že ESP32 bude číst změnu signálu na tomto tlačítku, které poté bude komunikovat s PC.
## Stav projektu 
Jelikož jsem blbec a rozbil jsem si druhý displej tak momentálně mám jenom jeden, tak pracuji pouze s tímto displejem. Momentálně se snažím vymyslet nějaký obrázek, který bude na displeji a poté se budu věnovat komunikaci ESP32 a PC. 
## Průběh práce na projektu
Ze začátku roku jsem zkouśel různé projekty napŕ.: ovládání diod pomocí tlačítek nebo přes cloud(viz kódy níže), poté jsem zkoušel programy s displejem, např.: teploměr DHT11 a na displeji se vypisovaly hodnoty z tohoto senzoru. Dále jsem zkoušel s 5 červenými diodami a 2 tlačítky udělat kód, který simuloval start 5 světel při motorsportových závodech, jedno tlačítko seplo postupné rozsvícení světel a druhé je vyplo, zde jsem se snažil využít interrupty, bohužel jsem se s tímto komandem toliká nenaučil a v žádném funkčním kódu ho ještě nemám. 
## Schémata
### Pro lepší zobrazení a čtení schémat jsem zvolil možnost ukázky zapojení, které jsem vytvořil na Wokwi.com. 
![image](https://github.com/Vajco06/Projekt1/assets/154622913/bda0052e-48dd-48d4-b043-1e01e8d0d1b1)

Schéma zapojení displeje 


![image0 (2)](https://github.com/Vajco06/Projekt1/assets/154622913/f6ab5f72-f40c-4224-b8a0-2ee1c3b87c09)
Zde je jak jsem zapojil displej (Ahoj, Pepik tam je, aby se něco vypsalo :D)


![image](https://github.com/Vajco06/Projekt1/assets/154622913/ea3c986a-a946-46ad-9ae5-4f275d0ec240)

Zde je chéma zapojení simulace závodních světel

## Kódy
### Zde budou kódy ke schématům uvedeným výše a kratší popis kódu. Omlouvám se, ale když jsem zde vložil kód, tak se to hodilo dohromady na 4 řádky, tak to raději pošlu jako screen.

![image](https://github.com/Vajco06/Projekt1/assets/154622913/50ed7cab-c0bb-40a7-bfe6-ea9a9ebc5007)

Toto je kód pro simulaci závodních světel. Tento kód funguje na funkci if, když se změní signál na tlačítku tak se spustí funkce a to samé s druhým tlačítkem.

![image](https://github.com/Vajco06/Projekt1/assets/154622913/008718c7-6508-4bfb-8cfc-3c61297cc57e)


Toto je kód na displej. V kódu se musí nadefinovat výška a šířka displeje a poté se už jenom nastavuje kurzor a co má napsat, ještě jsem se nenaučil kreslit. 

## Spolupracovníci
Celkově s pochopení ESP32 a HW k němu mi pomohl Míra Pich, Radim Krb a Dominik Bašek, konkrétně s Mírou a Dominikem jsem se snažil při hodinách pochopit zapojení displeje a Radim mi pomohl se naučit zezačátku roku s ESP32. Dále jsem ho používal ChatGPT, kde jsem si nechal vypsat kód, někdy poupravil, někdy nechal a podle toho jsem se učil. Poté jsem hodně čerpal ze stránek Arduino, kde jsem hlavně vyhledával funkce a použití různých komandů. 
## Zdroje
https://chat.openai.com  
https://www.arduino.cc     
https://wokwi.com 
