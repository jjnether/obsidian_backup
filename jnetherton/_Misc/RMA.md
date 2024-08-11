# RMA

Created: 2023-03-17 10:14:48 -0500

Modified: 2023-03-31 13:56:43 -0500

---

C&I RVP's

Stacey

Andy Best

Product code (item master combine sales code 2 and 3) ex. 8870

Can't use no update when updating sales order

Two types of JDE RMA pages (R8 warranty or R9 non-warranty)

-   If anything other than WD or WS, we can't create the sales order (Julie will help)

When filling out RMA, if you can't edit a line, cancel and re-edit

-   Select line, hit row at top, then cancel

Give Viper-HV and freight claim (damaged transportation, our freight company) RMA to Julie

PT - pole top




-   Write returning from, bill to, and ship to #'s
    -   Compare sales order to RMA form
        -   If it's the same, we can just copy the #'s
        -   If not, we have to look up the #'s in the address book (search customer address)
            -   Parent Number is Bill to
            -   Everything but alpha name is case sensitive
            -   Never use FC (former customer)
            -   If it doesn't exist, we'd use a temporary number and change later (64364)
-   Double check Rep #, P/N, and customer ID with sales order
-   Verify S/N (no previous RMA's)
-   Create PLRMA
    -   SG - switchgear
    -   CP - clip
    -   PT - PT
    -   CA - Cable accessories
    -   EL - electronics
    -   Item master -> Item number
        -   PLRMA(type of switch)(year)*
        -   PLRMAPT23*
            -   23 is for year '23
        -   Find next number free (ex. PLRMAPT23113)
            -   Write new number on RMA sheet (ex. PT23137)
        -   Make new PLRMA - TEMPLATE-RMA*
            -   Select proper template
                -   PT is SC 8
                -   SG is SC 7
            -   Copy and fill out necessary fields
            -   Change item number (PLRMA...)
            -   Change description and search text (INSP: S/N SWITCHTYPE e.g. INSP: 201502030044 VIP-ST)
            -   Next screen, then fix necessary sales categories
            -   Enter Location (GW)
            -   Enter cost (07, 08, 25)
        -   If editing PLRMA, change in both regular options and in branch



-   Create RMA
    -   Hit plus button
    -   Enter Bill to and Ship to #'s under Customer and Ship to
    -   Enter contact name (who the rep is and rep office) (ex. LINDHA SAGEN / PEAK MEASURE)
    -   Enter Claim/PO number (Original PO (RMA #)) (ex.
        -   Click in line field on bottom to generate RMA # (also write on RMA form)
        -   For non-warranty (SV), replace Original PO with "to follow"
    -   Enter fields at bottom
        -   Last disposition (REC)
        -   RMA item number (PLRMA #)
        -   Quantity
        -   Returned reason (usually ANA - analysis) (maybe INC - incorrect part)
        -   Expected receipt date (1 month domestic, 2 months international)
    -   PO # for receipt generated when hitting next line
        -   Write in OM # (PO # for Receipt) field on RMA form
    -   Start next line
        -   Usually S0P (warranty) or SHP
        -   Same almost everything
        -   Return reason OTH
        -   SO # will generate, then write on RMA form
        -   Warnings may come up, it's ok
    -   If non-warranty and a whole switch, need to add 2 additional lines (SHP MAT8 and SHP LAB8)
-   Under OM, right click -> PO -> PO Entry
    -   Change supplier to Returning from #
    -   Delete anything in certificate
    -   Payment terms - NC
    -   Verify dates (1 month apart for first 2 entries)
    -   On next screen, add attachment (hit order attachment)
        -   Create new text attachment, hit template button (top right)
        -   Create text attachment and use template (FRT* for freight)
            -   Prepaid or collect
            -   Fill out fields in text attachment, remove notes that don't apply
                -   Coyote for flatbed truck (> 95")
    -   Add text attachment (hit empty box next to Change Order on bottom)
        -   Enter catalog number, ID# and any additional instructions (also add "return SEL relay and cable" if needed)
-   Print RMA (Print Return Authorization G&W (OM))
    -   Data Selection -> Submit
    -   Change "1" to "literal" and for value, use OM#
    -   Automatically updates PO status to 400 (from 280)
    -   If you need to print again, use Reprint Return Authorization G&W (OM)
    -   If address is TO FOLLOW, place a physical label over the TO address, then write the returning from address and scan it
    -   Name file
        -   RMA# - OM# - SO# - SF# - Sales Rep # - Year - Month - Company (QTY) Switch Type
        -   Ex. (RMA11251 - OM628473 - SO110460 - SF77081 (55494-23-03) ARKANSAS VALLEY ELECTRIC COO (1) VIPER-SP
    -   Save to X:RGARGA return instructions
-   Update 525 to 529 (waiting for customer to return)
    -   Put in new SO#
    -   549 (RGA has received)
-   Email return instructions
    -   For Vipers, also have to attach crating guidelines
    -   Change subject line to add info (ex. GWRMA11274 - SO110632 - SF78515 CLECO VIPER-ST S/N 202004220058)
-   Scan RMA form, name same as return instruction, and save to X:RGARGA Completed Forms
-   Upload Both files to SO (in Work With Orders - SO - Detail)
    -   Hit SO hyperlink, then attachments
-   Input SO into SF
    -   Search S/N tab, then put in new SO, and hit RMA flag
-   In SF, update RMA# in resolution
-   Close SF Case
-   Update SO (for now, Julie will do this)



Trident is PC 72

-   Have to override PC 5 500 to 510 for non-gas



Attached is the return authorization and shipping guidelines for the customer.



SOLD TO

SHIP TO

CUSTOMER PO

ORDERED BY

REQUESTED DATE

SHIP TO ATTENTION



PAYMENT AND FREIGHT--

PAYMENT TERMS (NC FOR WARRANTY)

CARRIER NUMBER (57279 - BEST MEANS)

FREIGHT CODE fpp



St - hold code
