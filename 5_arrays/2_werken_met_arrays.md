## Nuttige array methoden

Net zoals we hebben gezien dat de Math-klasse een hele boel nuttige methoden in zich, zo ook heeft iedere array een aantal methoden waar handig gebruik van kan gemaakt worden.

Wanneer een array hebt gemaakt, dan kan je met de IntelliSense van Visual studio bekijken wat je allemaal kan doen met de array:

![](/assets/5_arrays/arrays2.png)


Al deze methoden hier beschrijven zal ons te ver nemen. De volgende methoden zijn echter zeer handig om te gebruiken:

Max(), Min(), Sum() en Average()

Volgende code geeft bijvoorbeeld het grootste getal terug uit een array genaamd "leeftijden":
```csharp
int oudsteleeftijd=leeftijden.Max();
```

## System.Array
Alle C# arrays erven over van de System.Array klasse (klasse en overerving zien we later dit semester), hierdoor kan je zaken zoals Length gebruiken op je array. De System.Array klasse heeft echter ook nog een hoop andere nuttige methoden zoals de BinarySearch(), Sort() en Reverse() methoden. Het gebruik hiervan is steeds dezelfde zoals volgende voorbeelden tonen:

### Arrays sorteren
Om arrays te sorteren roep je de Sort() methode op als volgt, als parameter geef je de array mee die gesorteerd moet worden.

Volgende voorbeeld toont hier het gebruik van:

```csharp
string[] myColors = { "red", "green", "yellow", "orange", "blue" };
//Sorteer
System.Array.Sort(myColors);
 
//Toon resultaat van sorteren
for (int i = 0; i < myColors.Length; i++)
{
    System.Console.WriteLine(myColors[i]);
}
```
Wanneer je de Sort-methode toepast op een array van string dan zullen de arrays alfabetisch gerangschikt worden.

### Arrays omkeren
Met de System.Array.Reverse() methode kunnen we dan weer de elementen van de array omkeren (dus het laatste element vooraan zetten en zo verder:

```csharp
System.Array.Reverse(myColors);
```

### Arrays leegmaken
Een array volledig leegmaken (alle elementen op ‘null’ zetten) doe je met de System.Array.Clear methode, als volgt:

```csharp
System.Array.Clear(myColors);
```
### Zoeken in arrays
De ``BinarySearch``-methode maakt het mogelijk om te zoeken naar de index van een gegeven element in een index. *Deze methode werkt enkel indien de elementen in de array gesorteerd staan!* Je geeft aan de methode 2 parameters mee, enerzijds de array in kwestie en anderzijds het element dat we zoeken. Als resultaat wordt de index van het gevonden element teruggegeven. Indien niets wordt gevonden zal het resultaat -1 zijn.

```csharp
System.Array.BinarySearch(myColors, "red" );
```
#### Manueel zoeken in arrays
Het zoeken in arrays kan met behulp van while of for-loops tamelijk snel. Volgende programmaatje gaat zoeken of het getal 12 aanwezig is in de array. Indien ja dan wordt de index bewaard van de positie in de array waar het getal staat:

```csharp
int teZoekenGetal = 12;
 
int[] getallen = { 5, 10, 12, 25, 16 };
 
bool gevonden = false;
int index = -1;
 
for (int i = 0; i < getallen.Length; i++)
{
    if (getallen[i] == teZoekenGetal)
    {
        gevonden = true;
        index = i;
    }
}
```
Voorgaande stukje code is de meest naïeve oplossing. Bedenk echter wat er gebeurt indien het getal dat we zoeken 2 of meerdere keren in de array staat. Index zal dan de positie bevatten van de laatst gevonden 12 in de array.

Het is zéér belangrijk dat je vlot dit soort algoritmen kan schrijven, zoals:

* Zoeken van elementpositie in array
* Tellen hoe vaak een element in een array voorkomt
* Elementen in een array 1 of meerdere plaatsen opschuiven,
