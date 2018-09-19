# Console-applicaties

Een console-applicatie is een  programma dat zijn in- en uitvoer via een klassiek commando/shell-scherm toont. Een console-applicatie draait  in dezelfde omgeving als wanneer we in Windows een command-prompt openen (via Start-> Uitvoeren-> ``cmd`` [enter] ). We zullen in deze cursus enkel console-applicaties leren maken. Grafische frontends (bv WPF) komen in deze cursus niet aan bod.

## ReadLine en WriteLine
Console-applicaties maken in C# vereist dat je minstens twee belangrijke C# methoden leert gebruiken:
Via **``Console.WriteLine()``** kunnen we tekst op het scherm tonen en met behulp van **``Console.ReadLine()``** kunnen we input van de gebruiker inlezen en in ons programma verwerken.

# Je eerste console programma
Maak een nieuw console-project aan (noem het Demo1) en open het Program.cs bestand (indien het niet open). **Veeg de code die hier reeds staat niet weg!**

Voeg binnen de accolades van ``Main`` volgende zin toe:

```csharp
Console.WriteLine("Hoi, ik ben het!");
Console.ReadKey();
```

Zodat je dus volgende code krijgt (:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Demo1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hoi, ik ben het!");
        }
    }
}
```
Compileer deze code en voer ze uit: druk hiervoor op het groene driehoekje met "Start" naast. Of via het menu Debug en dan Start Debugging.

**Let erop dat je iedere 'zin' eindigt met een kommapunt.**

## Analyse van de code
We gaan nu iedere lijn code kort bespreken. Sommige lijnen code zullen lange tijd niet belangrijk zijn.  Onthoud nu alvast dat: **alle belangrijke code staat tussen de accolades onder de lijn ``static void Main(string[] args)``**!

* ``using System;`` :  Alle ``Console``-commando's die we verderop gebruiken zitten in de ``System`` bibliotheek. Als we deze lijn (een zogenaamde **directive**) niet zouden schrijven dan moesten we ``System.Console.WriteLine`` i.p.v. ``Console.WriteLine`` schrijven verderop in de code. 
* Andere ``using`` directives: standaard zet Visual Studio de meest gebruikte bibliotheken reeds klaar. Veeg ze gerust weg als je zeker bent dat je bijvoorbeeld niets met Linq gaat doen. Bij twijfel: laten staan!
* ``namespace Demo1``: Dit is de unieke naam waarbinnen we ons programma zullen steken, en het is niet toevallig de naam van je project. Verander dit nooit tenzij je weet wat je aan het doen bent.
* ``class Program{}``: Hier start je echte programma. Alle code binnen deze Program accolades zullen gecompileerd worden naar een uitvoerbaar bestand.
* ``static void Main(string[] args)``: Het startpunt van iedere console-applicatie. Wat hier gemaakt wordt is een **methode** genaamd ``Main``. Je programma kan meerdere methoden (of functies) bevatten, maar enkel degene genaamd ``Main`` zal door de compiler als het startpunt van het programma gemaakt worden.
* ``Console.WriteLine("Hoi, ik ben het!");``: Dit is een **statement** dat de WriteLine-methode aanroept van de ``Console``-klasse. Het zal alle tekst die tussen de aanhalingstekens staat op het scherm tonen. 


 
 ## WriteLine: Tekst op het scherm
 De WriteLine-methode is een veelgebruikte methode in Console-applicaties. Het zorgt ervoor dat we tekst op het scherm kunnen tonen.

Voeg volgende lijn toe na de vorige WriteLine-lijn in je project:

``Console.WriteLine("Wie ben jij?!");`` 

De WriteLine methode zal alle tekst tonen die tussen de  "  " staan tussen de haakjes van de methode. **De aanhalingstekens aan het begin en einde van de tekst zijn uiterst belangrijk! Alsook het kommapunt helemaal achteraan.**

Je programma is nu:
```csharp
namespace Demo1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hoi, ik ben het!");
            Console.WriteLine("Wie ben jij?!");
        }
    }
}
```

> Oh boy...Wat was dit allemaal?! We hebben al aardig wat vreemde code zien passeren en het is niet meer dan normaal dat je nu denkt "dit ga ik nooit kunnen". Wees echter niet bevreesd: je zal sneller dan je denkt bovenstaande code als 'kinderspel' gaan bekijken. Een tip nodig? Test en experimenteer met wat je al kunt! 
