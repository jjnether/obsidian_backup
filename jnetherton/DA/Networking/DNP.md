-   Binary inputs are bits from the server (relay) to the client (SCADA)
-   Binary outputs are bits from the client to the server
- Binary Pair (a:b)
	- a - trip pulse
	- b - close pulse

Time Sync:
- By default, the SEL-700G accepts and ignores time set requests (TIMERQn = I for “ignore”). (This mode allows the SEL-700G to use a high accuracy, IRIG time source, but still interoperate with DNP3 masters that send time-synchronization messages.) You can set the SEL-700G to request time synchronization periodically by setting the TIMERQn setting to the desired period. You can also set it to not request, but accept, time synchronization (TIMERQn = M for “master”).