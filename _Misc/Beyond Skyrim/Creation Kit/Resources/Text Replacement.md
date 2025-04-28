Quests and quest-associated text can include the following tags:

## Tags

**<Alias=AliasName>**

-   This tag is replaced with the full name of the reference filling the alias AliasName.
-   In order to use this, you need to mark the specified alias as "Stores Text" (this indicates to the quest that the alias name needs to be saved onto the quest instance data).
-   If the resulting text is '\[...\]', then that means the alias wasn't filled.

**<Alias.Subtag=AliasName>**

-   Various subTag exists to give you additional parsing awesomeness, for example: <Alias.Race=Bob> would print "Nord" if Bob's race was NordRace
-   <Alias.ShortName=AliasName> -- the short name if it exists (otherwise just uses the normal full name).
-   <Alias.Race=AliasName> -- the race ("Nord", "Dark Elf", etc.)
-   <Alias.Pronoun=AliasName> -- pronoun ("he" or "she")
    -   <Alias.PronounObj=AliasName> -- pronoun object ("him" or "her")
    -   <Alias.PronounPos=AliasName> -- pronoun possessive ("his" or "hers")
    -   <Alias.PronounPosObj=AliasName> -- pronoun possessive ("his" or "her")
    -   <Alias.PronounRef=AliasName> -- pronoun reflexive("himself" or "herself")
    -   <Alias.PronounInt=AliasName> -- pronoun intensive("himself" or "herself")
        -   NOTE: in English reflexive and intensive pronouns are the same, I'm not sure they are in all languages though, so be careful. Examples:
            -   Intensive: "Bob himself was the one that did it." (emphasizes the noun Bob)
            -   Reflexive: "He saw himself in the mirror." (subject and object refers to the same person)

**<Relationship.Alias1=Alias2>**

-   You can parse relationship data from 2 aliases. For example: <Relationship.Sigrid=Dorthe> would print "Mother" if Sigrid is Dorthe's mother.

**<Alias.SubtagCap=AliasName>**

-   Adding "Cap" to the end of any subtag will cause it to be capitalized:
    -   "<Alias=Bob> ate <Alias.PronounPos=Bob> sandwich. <Alias.Pronoun_Cap_\=Bob> was happy." becomes:
    -   Bob ate his sandwich. **He** was happy.

**Automatic <Alias=Player> "text parsing alias"**

-   You can use <Alias=Player> and <Alias.Pronoun=Player> etc. WITHOUT needing to put the player in an alias.
-   Note that in order for this to work inside a Book, the book needs to have an active quest reference pointing to it (e.g. from the Quest Aliases tab of a quest of your choice).

**<Global=GlobalName>**

-   This tag is replaced with the value in global GlobalName at the start of the quest. Float globals are displayed to two decimal places.
-   In order to use this, you need to add the global to the list on the Quest Data tab.
-   The CURRENT VALUE of these globals will be saved to the current quest instance each time the quest starts.
-   If these values change during the quest, and you want the current quest instance to know about this change, use the function [UpdateCurrentInstanceGlobal\_-\_Quest](https://ck.uesp.net/wiki/UpdateCurrentInstanceGlobal_-_Quest "UpdateCurrentInstanceGlobal - Quest").

-   Subtags for Global.
    -   <Global.Hour12=GlobalName> -- Global based on GameDaysPassed parsed as hours on a 12-Hour scale.
    -   <Global.Minutes=GlobalName> -- Global based on GameDaysPassed parsed as minutes.
    -   <Global.Month=GlobalName> -- Global based on GameDaysPassed parsed as the current month expressed as a number
    -   <Global.MonthWord=GlobalName> -- Global based on GameDaysPassed parsed as the current month expressed as a word (e.g., First Seed, Midyear, Evening Star)
    -   <Global.Day=GlobalName> -- Global based on GameDaysPassed parsed as the current day.
    -   <Global.WeekDay=GlobalName> -- Global based on GameDaysPassed parsed as the current weekday (Morndas, Tirdas ,Middas, Turdas, Fredas, Loredas, Sundas)
    -   <Global.Year=GlobalName> -- Global based on GameDaysPassed parsed as the current year.
    -   <Global.TimeSpan=GlobalName> -- Global based on GameDaysPassed parsed as the current span of time (e.g., Afternoon, Morning, Evening)
    -   <Global.Meridiem=GlobalName> -- Global based on GameDaysPassed parsed as the current Meridiem time
-   There's a special subtag for timers
    -   <Global.Time=GlobalName> -- Global value parsed as "X Hours" for values greater than 1 or "X Minutes" for values less than 1.

**<BaseName>**

-   This tag is replaced with the original full name of the object. This only works when changing a ref alias's display text.

  
If a tag fails to parse for any reason (invalid format, invalid param, etc) the unparsed tag is displayed in the text instead.

### Example

For example, FreeformRiften04 has an objective:

```
"Find 20 nirnroot for Ingun Black-Briar (<Global=FFR04NirnCount>/<Global=FFR04NirnTotal>)"

```

This will be displayed as:

```
"Find 20 nirnroot for Ingun Black-Briar (0/20)"

```

Anytime FFR04NirnCount changes, a script needs to call:

```
FreeformRiften04.UpdateCurrentInstanceGlobal(FFR04NirnCount)

```

And then redisplay the objective. (The helper function [ModObjectiveGlobal](https://ck.uesp.net/wiki/ModObjectiveGlobal_-_Quest "ModObjectiveGlobal - Quest") can handle all of this in a single function call.)

### Where Used

Text replacement tags can be used in the following text fields:

-   Quest stage Log Entry
-   Quest objective Display Text
-   Topic prompts (but not [Topic Info](https://ck.uesp.net/wiki/Topic_Info "Topic Info"))
-   Messages - Title and Message Text
-   Book text

For Messages and Books, the base objects must be associated with a specific quest in order to use text replacement. For books, you must create an instance of the Book in a quest alias that is marked as "Uses Stored Text".

## Name replaced with Message

You can use a Message to replace the display name of anything in a quest's alias. Select a message on the "Display Name" dropdown on the [Alias window](https://ck.uesp.net/wiki/Quest_Alias_Tab "Quest Alias Tab"). The **Title** of the Message is used instead of the alias's normal name. The Message can use text replacement (see above), including the base name of the aliased object. This is how you'd rename a sword to "Bob's Iron Longsword" for example.