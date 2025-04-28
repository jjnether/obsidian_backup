## The Package Form

### Base Data

-   **ID:** The Package's Editor ID.
-   **Package Type:** Whether this form represents a Package or a [Package Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates").
-   **Owner Quest:** The quest this Package is associated with, if any.
    -   Only one Quest may be associated with each Package.
    -   Associating a Quest with a Package allows you to use the Quest's [Aliases](https://ck.uesp.net/wiki/Quest_Alias_Tab "Quest Alias Tab") as data inputs for the package. Note that you can always reference data from the Quest in [Conditions](https://ck.uesp.net/wiki/Conditions "Conditions").
-   **Combat Style:** The [Combat Style](https://ck.uesp.net/wiki/Combat_Style "Combat Style") the Actor should use while this package is active.
-   **Interrupt Override:** If this package is an [Interrupt Override](https://ck.uesp.net/wiki/Interrupt_Override_Packages "Interrupt Override Packages"), the type of override it is. Note that failing to set this field, then using the package as an override anyway may cause a crash.

### Package Tab

-   **Package Template:** The [Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates") this package inherits its Procedure Tree from.
-   **Public Package Data:** A list of data inputs exposed by the Package Template. For each, you can specify a new value in the **Selected Package Data** box on the right.
-   **Procedure Tree:** The Procedure Tree from the [Package Template](https://ck.uesp.net/wiki/Category:Package_Templates "Category:Package Templates"), for reference.

### Flags Tab

A list of the Package's flags, which specify modifiers to the behavior. See [Package Flags](https://ck.uesp.net/wiki/Package_Flags "Package Flags") for more details.

### Conditions

The list of [Conditions](https://ck.uesp.net/wiki/Conditions "Conditions") that must be satisfied for the Package to run.

### Schedule Tab

Sets the time at which the package will run. A Package's schedule acts like another [Condition](https://ck.uesp.net/wiki/Condition "Condition") in determining when and for how long a package will run.

-   The schedule cannot be in less than one hour blocks.
-   Day of week can be a specific day, all weekdays (Mon-Fri), the weekend (Sat and Sun), Mon/Wed/Fri or Tue/Thu.
-   Month can be a specific month or spring/summer/autumn/winter months.
-   As a rule, set either the Date and Month, or the Day of the Week, but not both.

### Begin/End/Change Tab

For each of the possible state changes of a package (Begin, End, Change) you can specify an Idle to be played, a Topic to be said, and [Papyrus Fragment](https://ck.uesp.net/wiki/Package_Fragments "Package Fragments") to run. The script is run first, so if you set a quest stage or variable in the script, the topic and idle will react to it.

-   The On End Idle only works for packages which have a "done" state.
-   If a package is marked Must Complete, the On End Idle will finish playing before starting the next package.