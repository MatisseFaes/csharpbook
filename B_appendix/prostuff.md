
# Handige Visual Studio code snippets

Bepaalde code zal je vaak opnieuw schrijven. Er zitten in VS tal van shortcuts om deze typische lijnen code sneller te schrijven. Schrijf een van volgende stukken code en druk dan 2x op de [tab]-toets
* cw: schrijft ``Console.WriteLine()``;
* for
* while
* dowhile
* switch
* propfull: full property
* prop: auto-property


# Bereik in code weten (Pro-kennis)
Het bereik van  datatypen is weliswaar opgegeven. Maar het is belangrijk om weten dat deze ook in de compiler gekend is. Het volgende voorbeeld toont dit aan:

```csharp
string zinnetje = "Het bereik van het type double is:";
Console.WriteLine(zinnetje + double.MinValue + " en " + double.MaxValue);
```

Je kan met andere woorden met `int.MaxValue` en `int.MinValue` het minimum- en maximumbereik van het type int verkrijgen. Wil je dit van een double, dan gebruik je `double.MaxValue` etc.

# Vreemde tekens in console tonen

Niets is zo leuk als de vreemdste tekens op het scherm tonen. In oude console-games werden deze tekens vaak gebruikt om *complexe* tekeningen op het scherm te tonen:
Om je filmpjes nog cooler te maken leggen we daarom uit hoe je dit kan tewerkstelligen, gebruikmakende van je kennis over converteren.
![](/assets/0_intro/kerosenethunder_mockup.png)

## Unicode karakters tonen

Zonder een uitleg te geven over het verschil tussen ASCII en Unicode is het vooral belangrijk te weten dat je best met Unicode werkt.

1. Zoek het teken\(s\) dat je nodig hebt in een Unicode-tabel \([Deze is handig](https://unicode-table.com/en/)\)
2. Plaats bovenaan je Main: `Console.OutputEncoding = System.Text.Encoding.UTF8;`
3. Je kan nu op 2 manieren dit teken in console plaatsen

### Manier 1: copy/paste

Kopieer het karakter zelf en plaats het in je code waar je het nodig hebt, bijvoorbeeld:

```rust
Console.WriteLine("˧");
```

### Manier 2: hexadecimale code casten naar char

Noteer de hexadecimale code van het karakter dat in de tabel staat.

![](/assets/0_intro/letter.jpg)

In dit geval is de code 0x02e7.

Om dit teken te tonen schrijf je dan:

```csharp
char blokje = (char)0x02e7;
Console.WriteLine(blokje);
```

In C\# schrijf je hexadecimale getallen als volgt als je ze rechstreeks in een string wilt plaatsen: \u02e7

Wil je dus bovenstaande teken schrijven dan kan dan ook als volgt:

```csharp
Console.WriteLine("\u02e7");
```


