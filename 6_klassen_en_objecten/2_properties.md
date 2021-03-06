# Properties

## In een wereld zonder properties 
Properties (*eigenschappen*) zijn de C# manier om objecten hun interne staat in en uit te lezen.
Ze zorgen voor een gecontroleerde toegang tot de interne structuur van je objecten.

Stel dat we volgende klasse hebben:
```csharp
class SithLord
{
    private int energy;
    private string sithName;
}
```
Een ``SithLord`` heeft steeds een verborgen Sith Name en ook een hoeveelheid energie die hij nodig heeft om te strijden.
**Het is uit den boze dat we eenvoudige data fields (``energy`` en ``name``) ``public`` maken.** Zouden we dat wel doen dan kunnen externe objecten deze geheime informatie uitlezen!
```csharp
SithLord Palpatine= new SithLord();
Console.WriteLine(Palpatine.sithName);
```

We willen echter wel van buitenuit het energy-level van een sithLord kunnen instellen. Maar ook hier hetzelfde probleem: wat als we de enrgy-level op -1000 instellen? Terwijl energy nooit onder 0 mag gaan.

**Properties lossen dit probleem op**

## Full properties

Een **full property** ziet er als volgt uit:
```csharp
class SithLord
{
    private int energy;
    private string sithName;

    public int Energy
    {
        get
        {
            return energy;
        }
        set
        {
            energy=value;
        }
    }
}
```

We zullen de property stuk per stuk analyseren:
* ``public int Energy``: een property is altijd ``public``. Vervolgens zeggen we wat voor type de property moet zijn en geven we het een naam. Indien je de property gaat gebruiken om een intern dataveld naar buiten beschikbaar te stellen, dan is het een goede gewoonte om dezelfde naam als dat veld te nemen maar nu met een hoofdletter. (dus ``Energy`` i.p.v. ``energy``).
* { }: Vervolgens volgen 2 accolades waarbinnen we de werking van de property beschrijven.
* ``get {}``: indien je wenst dat de property data **naar buiten** moet sturen, dan schrijven we de get-code. Binnen de accolades van de get schrijven we wat er naar buiten moet gestuurd worden. In dit geval ``return energy`` maar dit mag even goed bijvoorbeeld ``return 4`` of een hele reeks berekeningen zijn. Het element dat je returnt in de get code moet uiteraard van hetzelfde type zijn als waarmee je de property hebt gedefinieerd (``int`` in dit geval).
    * We kunnen nu van buitenaf toch de waarde van ``energy`` uitlezen via de property en het get-gedeelte: ``Console.WriteLine(Palpatine.Energy);``
* set{}: in het set-gedeelte schrijven we de code die we moeten hanteren indien men van buitenuit een waarde aan de property wenst te geven om zo een interne variabele aan te passen. De waarde die we van buitenuit krijgen (als een parameter zeg maar) zal **altijd** in een lokale variabele ``value`` worden bewaard. Deze zal van het type van de property zijn. Vervolgens kunnen we ``value`` toewijzen aan de interne variabele indien gewenst: ``energy=value`` 
    * We kunnen vanaf nu van buitenaf waarden toewijzen aan de property en zo ``energy``vtoch bereiken: ``Palpatine.Energy=50``.

### Snel property schrijven
Visual Studio heeft een ingebouwde shortcut om snel een full property, inclusief een bijhorende private dataveld, te schrijven. **Typ ``propfull`` gevolgd door twee tabs!**

## Full property met toegangscontrole
De full property ``Energy`` heeft nog steeds het probleem dat we negatieve waarden kunnen toewijzen (via de ``set``) die dan vervolgens zal toegewezen worden aan ``energy``.
> Properties hebben echter de mogelijkheid om op te treden als wachters van en naar de interne staat van objecten.

We kunnen in de ``set``code extra controles inbouwen. Asl volgt:
```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
        set
        {
            if(value>=0)
                energy=value;
        }
    }
```
Enkel indien de toegewezen waarde groter of gelijk is aan 0 zal deze ook effectief aan ``energy`` toegewezen worden.
Volgende lijn zal dus geen effect hebben:
`` Palpatine.Energy=-1;``

We kunnen de code binnen ``set`` (en ``get``) zo complex als we willen maken.

## Property variaties
We zijn niet verplicht om zowel de ``get`` en de ``set`` code van een property te schrijven. 

### Read-only property
```csharp
   public int Energy
    {
        set
        {
            if(value>=0)
                energy=value;
        }
    }
```
We kunnen dus enkel ``energy`` uitlezen, maar niet van buitenuit aanpassen.

### Write-only property
```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
    }
```
We kunnen dus enkel ``energy`` een waarde geven, maar niet van buitenuit uitlezen.

### Read-only property met private set
Soms gebeurt het dat we van buitenuit enkel de gebruiker de property read-only willen maken. We willen echter intern (in de klasse zelf) nog steeds controleren dat er geen illegale waarden aan private datafields worden gegeven. Op dat moment definieren we een read-only property met een private setter:

```csharp
   public int Energy
    {
        get
        {
            return energy;
        }
        private set
        {
            if(value>=0)
                energy=value;
        }
    }
```
Van buitenuit zal enkel code werken die de``get``-`van deze property aanroept: ``Console.WriteLine(Palpatine.Energy);``. Code die de ``set`` van buitenuit nodig heeft zal een fout geven zoals: ``Palpatine.Energy=65``; ongeacht of deze geldig is of niet.

**Nu goed opletten**: indien we in het object de property willen gebruiken dan moeten we deze dus ook effectief aanroepen, anders omzeilen we hem als we rechtstreeks ``energy`` instellen.

Kijk zelf naar volgende **slechte** code:
```csharp
class SithLord
{
    private int energy;
    private string sithName;

    public void ResetLord()
    {
        energy=-1;
    }

    public int Energy
    {
        get
        {
            return energy;
        }
        private set
        {
            if(value>=0)
                energy=value;
        }
    }
}
```

De nieuw toegevoegde methode ``ResetLord`` willen we gebruiken om de lord z'n energy terug te verlagen. Door echter ``energy=-1`` te schrijven geven we dus -1 rechtstreeks aan ``energy``. Nochtans is dit een illegale waarden.
We moeten dus in de methode ook expliciet via de property gaan en dus schrijven:
```csharp
public void ResetLord()
{
    Energy=-1; // Energy i.p.v. energy
}
```

> **Het is een goede gewoonte om zo vaak mogelijk via de properties je interne variabele aan te passen en niet rechtstreeks het dataveld zelf.**

### REad-only Get-omvormers
Je bent uiteraard niet verplicht om voor iedere interne variabele een bijhorende property te schrijven. Omgekeerd ook: mogelijk wil je extra properties hebben voor data die je 'on-the-fy' kan genereren.

Stel dat we volgende klasse hebben
```csharp
class Persoon
{
    private string voornaam;
    private string achternaam;
}
```
We willen echter ook soms de volledige naam op het scherm tonen ("Voornaam + Achternaam"). Via een read-only property kan dit supereenvoudig:
```csharp
class Persoon
{
    private string voornaam;
    private string achternaam;
    public string FullName
    {
        get{ return $"{voornaam} {achternaam}";}
    }
}
```

Of nog eentje:
```csharp
class Aarde
{
    public double ZwaarteKracht
    {
        get
        {
            return 9.81;
        }
    }
}
```

Nog een voorbeeldje:

```csharp
class Persoon
{
    private int age;

    public bool IsWaarschijnlijkNogLevend
    {
        get
        {
            if(age>120) return false;
            return true;
        }
    }
}
```

Vaak gebruiken we dit soort read-only properties om data te transformeren. Stel bijvoorbeeld dat we volgende klasse hebben:
```csharp
class Persoon
{
    private int age; //in jaren

    public int  LeeftijdInMaanden
    {
        get
        {
            return age*12;
        }
    }
}
```