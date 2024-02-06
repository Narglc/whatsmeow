# xml 编解码 帮助

```bash
const (
	ListEmpty   = 0
	Dictionary0 = 236	// EC
	Dictionary1 = 237	// ED
	Dictionary2 = 238	// EE
	Dictionary3 = 239	// EF
	InteropJID  = 245	// F5
	FBJID       = 246	// F6
	ADJID       = 247	// F7
	List8       = 248	// F8
	List16      = 249	// F9
	JIDPair     = 250	// FA
	Hex8        = 251	// FB
	Binary8     = 252	// FC
	Binary20    = 253	// FD
	Binary32    = 254	// FE
	Nibble8     = 255	// FF
)
----
F8 10
09		- notification
06		- from?
FA FF 0 9			- [FA - JIDPair]
120363216419776256	- gid
1C		- g.us
04		- type
EC 20	- w:gp2 [Dictionary0]
08		- id
FB 05	- [Hex8 len]
3016845129		- id-no
05	- participant
FA FF 8 7			- [FA - JIDPair]
8613714726970	- phone
F				- phone 补位
03				- s.whatsapp.net
FC 0F	- [0F-15*2 len; FC-Binary8]
61646472657373696E675F6D6F6465	- addressing_mode
EC 51	- pn [Dictionary0]
18		- notify
FC 0F	- [0F-15*2 len; FC-Binary8]
E69993E5AE87E9A39EE9A39EE9A39E	- 晓宇飞飞飞
1A		- t
FF 05	- [FF-Nibble8?]
1707199935		- 时间戳 明文
F8 01	- [F8-List8]
F8 02	- [F8-List8]
EC 3C	- member_add_mode
FC 0E	- [0E-14*2 len; FC-Binary8]
616C6C5F6D656D6265725F616464	- all_member_add

<notification addressing_mode="pn" from="120363216419776256@g.us" id="3016845129" notify="晓宇飞飞飞" participant="8613714726970@s.whatsapp.net" t="1707199935" type="w:gp2">
	<member_add_mode>all_member_add</member_add_mode>
</notification>
----
F8 10
09		- notification
06		- from?
FA FF 09			- [FA - JIDPair]
120363216419776256	- gid
1C		- g.us
04		- type
EC20	- w:gp2
08		- id
FB 05	- [Hex8 len]
2203164294		- id-no
05	- participant
FA FF 8 7			- [FA - JIDPair]
8613714726970	- phone
F				- phone 补位
03				- s.whatsapp.net
FC 0F	- [0F-15*2 len; FC-Binary8]
61646472657373696E675F6D6F6465	- addressing_mode
EC 51	- pn [Dictionary0]
18		- notify
FC 0F	- [0F-15*2 len; FC-Binary8]
E69993E5AE87E9A39EE9A39EE9A39E	- 晓宇飞飞飞
1A		- t
FF 05	- [FF-Nibble8?]
1707199939		- 时间戳 明文
F8 01	- [F8-List8]
F8 02	- [F8-List8]
EC 3C	- member_add_mode
FC 09	- [09-09*2 len; FC-Binary8]
61646D696E5F616464	- admin_add
<notification addressing_mode="pn" from="120363216419776256@g.us" id="2203164294" notify="晓宇飞飞飞" participant="8613714726970@s.whatsapp.net" t="1707199939" type="w:gp2">
	<member_add_mode>admin_add</member_add_mode>
</notification>

----
token:notification, type:single index:9
token:addressing_mode not found.
token:pn, type:double dictNo:EC, index:51
token:g.us, type:single index:1C
token:from, type:single index:6
token:id, type:single index:8
token:notify, type:single index:18
token:participant, type:single index:5
token:t, type:single index:1A
token:type, type:single index:4
token:member_add_mode, type:double dictNo:EC, index:3C
token:all_member_add not found.
token:s.whatsapp.net, type:single index:3
token:w:gp2, type:double dictNo:EC, index:20
120363216419776256--->:313230333633323136343139373736323536
1787767991--->:31373837373637393931
晓宇飞飞飞--->:E69993E5AE87E9A39EE9A39EE9A39E
8613714726970--->:38363133373134373236393730
1707198298--->:31373037313938323938
all_member_add--->:616C6C5F6D656D6265725F616464
admin_add--->:61646D696E5F616464
addressing_mode--->:61646472657373696E675F6D6F6465
```