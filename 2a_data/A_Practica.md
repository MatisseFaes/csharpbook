# Euro naar dollar
Ontwerp een toepassing waarmee je een ingevoerd bedrag, inclusief komma-getallen  in euro kan omrekenen naar dollar. Gebruik hierbij de huidige wisselkoers
Je hoeft niet af te ronden. Het resultaat in een label wordt als volgt weergegeven: ``X EUR is gelijk aan Y USD``.


# Feestkassa
De plaatselijke voetbalclub organiseert een mosselfestijn. Naast mosselen met frietjes (20 EUR) bieden ze voor de kinderen de mogelijkheid om een koninginnehapje (10 EUR) te kiezen. Verder is er een ijsje als nagerecht voorzien (3 EUR). Om het gemakkelijk te maken kosten alle dranken 2 EUR.


Ontwerp een applicatie zodat de vrijwilliger aan de kassa alleen maar de juiste aantallen moet ingeven ,lijn per lijn. (frietjes, koninginenhapje, ijsje, drank) om de totaal te betalen prijs te berekenen. 

Het resultaat wordt als volgt weergegeven: ``Het totaal te betalen bedrag is x EU``.

# Systeem informatie
## Deel 1
Maak een applicatie die de belangrijkste computer-informatie (geheugen, etc) aan de gebruiker toont.

Deze computer-informatie kan je verkrijgen mbv de Environment-klasse. Hier enkele voorbeelden (kijk zelf of er nog nuttige properties over je computer in staan):
```csharp
            bool is64bit = Environment.Is64BitOperatingSystem;
            string pcname = Environment.MachineName;
            int proccount = Environment.ProcessorCount;
            string username = Environment.UserName;
            long memory = Environment.WorkingSet; //bytes
```

Zoals je ziet wordt het geheugen in bytes teruggegeven. Zorg ervoor dat het geheugen steeds in mega of gigabytes op het scherm wordt getoond.

Formateer de informatie met behulp van de $-notatie  zodat deze  deftig getoond wordt.

## Deel 2

Ook informatie over de harde schijven kan je verkrijgen (in bits)
```csharp
            long cdriveinbytes = DriveInfo.GetDrives()[0].AvailableFreeSpace;  
            long totalsize = DriveInfo.GetDrives()[0].TotalSize;  
```
De 0 tussen rechte haakjes is de index van welke schijf je informatie wenst. 0 is de eerste harde schijf, 1 de tweede, enzovoort. (Ter info: dit zijn arrays, zie later)

Vraag aan de gebruiker het nummer van de harde schijf waar meer informatie over moet getoond worden. 

Opgelet: sta toe dat de gebruiker 1 voor de eerste harde schijf mag gebruiken, 2 voor de tweede, enzovoort. Je zal dus in code nog manueel 1 moeten aftrekken van de invoer van de gebruiken.
Bv:
```csharp
int invoer= Convert.ToInt(Console.ReadLine()) - 1 ;
 long totalsize = DriveInfo.GetDrives()[invoer].TotalSize;  
 ```

 # Het Orakel van Delphi
 Gebruik de random generator om een orakel/waarzegger te maken. Het programma zal aan de gebruiker vertellen hoe lang deze nog zal leven. Bijvoorbeeld: "Je zal nog 15 jaar leven.".