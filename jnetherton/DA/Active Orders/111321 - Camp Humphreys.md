
[file path](<file:///C:\Users\jnetherton\G&W Electric Co\US-PowerGridAutomation - Documents\_Lazer\Camp Humphreys (KK Interlock) - 111321>)

- FAT doc
	- explain in detail
	- scope
	- lots of pictures
	- send to woody/tom
- Prepare 351S program

- For Way 3 open/close, indication is only through PB LED's, not display points - I assume this is fine?
- Check PB layout if it's ok?
- I'll leave remote enabled PB for LED indication even though PB doesn't do anything because of selector switch
	- this ok?
- PB lock says hold for 3 sec, but logic doesn't really show any timer
- Voltage Live DP used to be logic from an input contact. Ok to leave out, or do I use 59 element somehow?
- Batt test is on 8 hour timer, that ok?
- Lockout equation - should any trips put switch in lockout?
	- does there need to be a lockout?
	- consists of:
		- low sf6
		- open fail
		- close/open fail
		- 51p2 trip
		- 51g2 trip
- Can't trip with PB if low SF6 (can still trip with O/C)
- O/C is just 2x51P and 2x51G
	- any 50 elements?

Kirk Keys:
- TNI
	- Way 1
		- 2 cylinders
		- 1 key can be withdrawn when locked in open position
	- Way 2
		- 1 cylinder
		- key can be withdrawn when locked in open position
- GNI
	- Way 2/3/4
		- 1 cylinder
		- key can be withdrawn when locked in open position

![[Pasted image 20240823151508.png|700]]