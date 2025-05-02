Script objects recognized by Papyrus and their associated [functions](https://ck.uesp.net/wiki/Function_Reference "Function Reference"), [properties](https://ck.uesp.net/wiki/Property_Reference "Property Reference") and [events](https://ck.uesp.net/wiki/Events_Reference "Events Reference").

## About Extended Script Objects

More specific script objects are based on more general ones. Typically more specific objects are called children and the more general ones are called parents. Script children inherit certain qualities from their parents. For example, [Actor Script](https://ck.uesp.net/wiki/Actor_Script "Actor Script") has access to all the events and functions listed on [ObjectReference Script](https://ck.uesp.net/wiki/ObjectReference_Script "ObjectReference Script"), and [Form Script](https://ck.uesp.net/wiki/Form_Script "Form Script") even though they aren't all listed on Actor Script.

Read more about [Extending Scripts](https://ck.uesp.net/wiki/Extending_Scripts_(Papyrus) "Extending Scripts (Papyrus)")

## Map

Here is the Papyrus script object map. You can also use the "**Extends:** xxxx" link on the top of each script object page to find its parent. Scripts in _italics_ are added by SKSE.

```
------------------------------------------------------------------------------
|-ActiveMagicEffect   |-Debug    |-Form   |-ColorComponent   |-ModEvent      |-StringUtil
|-Alias               |-Game        |     |-FormType         |-NetImmerse    |-UI
   |-ReferenceAlias   |-Math        |     |-GameData         |-SKSE          |-UICallback  
   \-LocationAlias    |-Utility     |     |-Input            |-SpawnerTask   \-WornObject
                                    |                                        
           -------------------------|----------------------------
           |-Action                 |-Hazard                    |-Potion 
           |-Activator              |-HeadPart                  |-Projectile
           |   |-Flora              |-Idle                      |-Quest
           |   |-Furniture          |-ImageSpaceModifier        |   \-Stage Fragments
           |   \-TalkingActivator   |-ImpactDataSet             |-Race
           |-ActorBase              |-Ingredient                |-Scene
           |-ActorValueInfo         |-Keyword                   |   |-Phase Fragments
           |-Ammo                   |   \-LocationRefType       |   |-Scene Fragments
           |-Armor                  |-LeveledActor              |   \-Timer Fragments
           |-ArmorAddon             |-LeveledItem               |-Scroll
           |-Art                    |-LeveledSpell              |-Shout
           |-AssociationType        |-Light                     |-Sound
           |-Book                   |-Location                  |-SoundCategory
           |-Cell                   |-MagicEffect               |-SoundDescriptor
           |-Class                  |-Message                   |-Spell
           |-ColorForm              |-MiscObject                |-Static
           |-CombatStyle            |   |-Apparatus             |-TextureSet
           |-Container              |   |-ConstructibleObject   |-Topic
           |-DefaultObjectManager   |   |-Key                   |-TopicInfo        
           |-Door                   |   \-SoulGem               |   \-Info Fragments
           |-EffectShader           |-MusicType                 |-TreeObject
           |-Enchantment            |-ObjectReference           |-VisualEffect
           |-EncounterZone          |   \-Actor                 |-VoiceType
           |-EquipSlot              |-Outfit                    |-Weapon
           |-Explosion              |-Package                   |-Weather
           |-Faction                |   \-Package Fragments     |-WordOfPower
           |-FormList               |-Perk                      \-WorldSpace
           |-GlobalVariable             \-Perk Fragments        

```