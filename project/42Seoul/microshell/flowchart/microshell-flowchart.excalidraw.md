---

excalidraw-plugin: raw
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
start
parse_line으로부터 parse_list를 넘겨받는다. ^TdAlpDw3

pipe_fd, pipe_fd_2, first_cmd를 초기화 ^CpOgMOAQ

loop ^aQAwrp0Y

no ^1mwFaf2j

node의 type이 무엇인가? ^OyqaaS8l

CMD ^YfcFH3Vm

PIPE ^kDdUqVXE

SEM ^SRPVMbzL

wait_child_end 후 child_num, first_cmd를 원상복구 ^CGSCc1Tz

첫번째 cmd인가? ^ixOzTW7m

yes ^ImKQfSgh

no ^NtthsPTB

cmd 뒤에  PIPE가 
존재하는가? ^3ghEIm5q

yes ^XYYrdpbF

1. pipe 하나를 열고 fork
2. 자식에서 표준 출력을 pipe의 WRITE로 redirection, execve로 cmd를 실행한다.  ^xhAb0NSv

no ^Mw7TQbMl

cmd가 cd인가? ^KxjWML7L

yes ^MDrJZHS7

ft_cd 실행 ^ZN1naXKl

no ^yNlahHJ6

자식 프로세스에서 cmd 실행 ^MJH5dMK2

마지막 cmd인가? ^yGrokf01

no(mid cmd) ^T7v2dtmS

yes ^tLIPMmca

1. 자식 프로세스를 연다.
2. 표준 입력을 pipe로 redirection, cmd를 실행 ^u61wo1qW

1. 두번째 pipe를 열고 fork
2. 첫번째 pipe로 표준 입력을 redirection, 두번째 pipe로 표준 출력을 redirection, cmd를 실행 ^gbvsKCeG

go_to_next_node ^ImpBiiGL

parse_list의 끝에 도달하였는가? ^mvIk1Ww6

no ^x9B0h64y

yes ^8Knk1zfn

end ^NUXNTJc4

[[parse_line-flowchart.excalidraw]] ^eCJMh6R5

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.0.25",
	"elements": [
		{
			"id": "eCJMh6R5",
			"type": "ellipse",
			"x": -139.38215255737305,
			"y": -414.77381896972656,
			"width": 268.2359924316406,
			"height": 156,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1104327123,
			"version": 249,
			"versionNonce": 1513695731,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "TdAlpDw3"
				},
				{
					"id": "9SRhzMqmd_vlpfAC2_VK_",
					"type": "arrow"
				}
			],
			"updated": 1718677269129,
			"link": "[[parse_line-flowchart.excalidraw]]",
			"locked": false
		},
		{
			"id": "TdAlpDw3",
			"type": "text",
			"x": -89.71982739754773,
			"y": -386.92814790227726,
			"width": 169.23985290527344,
			"height": 100,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1442734803,
			"version": 303,
			"versionNonce": 1622991549,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "start\nparse_line으로부터\nparse_list를\n넘겨받는다.",
			"rawText": "start\nparse_line으로부터 parse_list를 넘겨받는다.",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 92,
			"containerId": "eCJMh6R5",
			"originalText": "start\nparse_line으로부터 parse_list를 넘겨받는다.",
			"lineHeight": 1.25
		},
		{
			"id": "9SRhzMqmd_vlpfAC2_VK_",
			"type": "arrow",
			"x": -4.250432650831772,
			"y": -253.5864140735398,
			"width": 1.2298121398438413,
			"height": 31.56460715083614,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1428277011,
			"version": 170,
			"versionNonce": 1307094290,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323643,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-1.2298121398438413,
					31.56460715083614
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "eCJMh6R5",
				"gap": 5.1896074898096884,
				"focus": -0.032079143848022525
			},
			"endBinding": {
				"elementId": "yyJ8PnOt1EVY-tsv5AtgY",
				"gap": 12.673828125,
				"focus": -0.00039313298677009367
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "yyJ8PnOt1EVY-tsv5AtgY",
			"type": "rectangle",
			"x": -128.9133415222168,
			"y": -209.34797879770366,
			"width": 243.53030395507812,
			"height": 62.75390625,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1302951859,
			"version": 175,
			"versionNonce": 1139507997,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "9SRhzMqmd_vlpfAC2_VK_",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "CpOgMOAQ"
				},
				{
					"id": "cFyqHOnf8HhtEl1cSmIhP",
					"type": "arrow"
				}
			],
			"updated": 1718677269129,
			"link": null,
			"locked": false
		},
		{
			"id": "CpOgMOAQ",
			"type": "text",
			"x": -105.32809066772461,
			"y": -202.97102567270366,
			"width": 196.35980224609375,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1320650003,
			"version": 144,
			"versionNonce": 1691846963,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "pipe_fd, pipe_fd_2,\nfirst_cmd를 초기화",
			"rawText": "pipe_fd, pipe_fd_2, first_cmd를 초기화",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "yyJ8PnOt1EVY-tsv5AtgY",
			"originalText": "pipe_fd, pipe_fd_2, first_cmd를 초기화",
			"lineHeight": 1.25
		},
		{
			"id": "cFyqHOnf8HhtEl1cSmIhP",
			"type": "arrow",
			"x": -5.328349783485435,
			"y": -145.59407254770366,
			"width": 1.808730838205661,
			"height": 39.226367650681794,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 228947091,
			"version": 761,
			"versionNonce": 2131268626,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323643,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					1.808730838205661,
					39.226367650681794
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "yyJ8PnOt1EVY-tsv5AtgY",
				"gap": 1,
				"focus": -0.002651186709501108
			},
			"endBinding": {
				"elementId": "eMRLaDVmsHbOypzWeesJz",
				"gap": 9.00855457447625,
				"focus": 0.05782618825015232
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "eMRLaDVmsHbOypzWeesJz",
			"type": "diamond",
			"x": -185.35854721069336,
			"y": -99.25081082895366,
			"width": 349.64854431152344,
			"height": 120,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 819178653,
			"version": 512,
			"versionNonce": 1964485501,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "cFyqHOnf8HhtEl1cSmIhP",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "aQAwrp0Y"
				},
				{
					"id": "8Mxo_eQ0Nam1UPacnFzWk",
					"type": "arrow"
				},
				{
					"id": "N2VeoGExp6ra7tzslX25q",
					"type": "arrow"
				}
			],
			"updated": 1718677447280,
			"link": null,
			"locked": false
		},
		{
			"id": "aQAwrp0Y",
			"type": "text",
			"x": -29.086387634277344,
			"y": -51.75081082895366,
			"width": 37.27995300292969,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1302912157,
			"version": 595,
			"versionNonce": 1338143389,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677412132,
			"link": null,
			"locked": false,
			"text": "loop",
			"rawText": "loop",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "eMRLaDVmsHbOypzWeesJz",
			"originalText": "loop",
			"lineHeight": 1.25
		},
		{
			"id": "8Mxo_eQ0Nam1UPacnFzWk",
			"type": "arrow",
			"x": -7.00263897220577,
			"y": 26.06312406516105,
			"width": 0.022555945500537966,
			"height": 55.35664415641773,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1062958653,
			"version": 151,
			"versionNonce": 1510983890,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "1mwFaf2j"
				}
			],
			"updated": 1718685323643,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-0.022555945500537966,
					55.35664415641773
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "eMRLaDVmsHbOypzWeesJz",
				"gap": 6.172589051010014,
				"focus": -0.020371026231501714
			},
			"endBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"gap": 10.434630559042944,
				"focus": -0.0017333007232181675
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "1mwFaf2j",
			"type": "text",
			"x": -17.126354217529297,
			"y": 47.40434053823384,
			"width": 20.41998291015625,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1151589875,
			"version": 12,
			"versionNonce": 1231131155,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "no",
			"rawText": "no",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "8Mxo_eQ0Nam1UPacnFzWk",
			"originalText": "no",
			"lineHeight": 1.25
		},
		{
			"id": "N0bwk0I_LBNWpL3Pkpm_P",
			"type": "diamond",
			"x": -157.6782341003418,
			"y": 91.85181627808157,
			"width": 301.7703552246094,
			"height": 123.3980712890625,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 540203987,
			"version": 171,
			"versionNonce": 616991901,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "8Mxo_eQ0Nam1UPacnFzWk",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "OyqaaS8l"
				},
				{
					"id": "aH3qXnAfHNMcsOWqjBFCy",
					"type": "arrow"
				},
				{
					"id": "4HDKNULTh5shvcL1dblCx",
					"type": "arrow"
				},
				{
					"id": "fiM2lTLJTs5SjZrAZ9Omg",
					"type": "arrow"
				}
			],
			"updated": 1718677269129,
			"link": null,
			"locked": false
		},
		{
			"id": "OyqaaS8l",
			"type": "text",
			"x": -71.14558792114258,
			"y": 128.7013341003472,
			"width": 128.81988525390625,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1221859603,
			"version": 94,
			"versionNonce": 1512822707,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "node의 type이\n무엇인가?",
			"rawText": "node의 type이 무엇인가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "N0bwk0I_LBNWpL3Pkpm_P",
			"originalText": "node의 type이 무엇인가?",
			"lineHeight": 1.25
		},
		{
			"id": "aH3qXnAfHNMcsOWqjBFCy",
			"type": "arrow",
			"x": -156.53715133666987,
			"y": 157.46448717651907,
			"width": 441.29800733983456,
			"height": 148.1502550365247,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 356529331,
			"version": 545,
			"versionNonce": 1514014098,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "YfcFH3Vm"
				}
			],
			"updated": 1718685323644,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-387.02279832628057,
					6.233690049913207
				],
				[
					-441.29800733983456,
					148.1502550365247
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"gap": 3.190586762384541,
				"focus": -0.024339771926068444
			},
			"endBinding": {
				"elementId": "5pQRl2SNRgr3eUBGu9Jsu",
				"gap": 8.16116270699137,
				"focus": 0.5860440844261984
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "YfcFH3Vm",
			"type": "text",
			"x": -284.4603157043457,
			"y": 153.34430895386282,
			"width": 43.79997253417969,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1171712691,
			"version": 20,
			"versionNonce": 1215809885,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "CMD",
			"rawText": "CMD",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "aH3qXnAfHNMcsOWqjBFCy",
			"originalText": "CMD",
			"lineHeight": 1.25
		},
		{
			"id": "4HDKNULTh5shvcL1dblCx",
			"type": "arrow",
			"x": -3.5124320983886714,
			"y": 217.44294176636285,
			"width": 0.834485516793078,
			"height": 267.69310538396985,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 198189693,
			"version": 73,
			"versionNonce": 1885507282,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "kDdUqVXE"
				}
			],
			"updated": 1718685323648,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					0.834485516793078,
					267.69310538396985
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"gap": 3.271592090890721,
				"focus": -0.020422497706963652
			},
			"endBinding": {
				"elementId": "EU1enNzAFnkDWZEu8g_CW",
				"gap": 21.813903248459276,
				"focus": -0.0858530331159585
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "kDdUqVXE",
			"type": "text",
			"x": -28.91348648071289,
			"y": 244.5600987487847,
			"width": 50.81996154785156,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1652306739,
			"version": 9,
			"versionNonce": 1288738237,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "PIPE",
			"rawText": "PIPE",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "4HDKNULTh5shvcL1dblCx",
			"originalText": "PIPE",
			"lineHeight": 1.25
		},
		{
			"id": "5pQRl2SNRgr3eUBGu9Jsu",
			"type": "diamond",
			"x": -752.77245203654,
			"y": 256.26475903966264,
			"width": 179.18951416015625,
			"height": 165.82635498046875,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1696028157,
			"version": 404,
			"versionNonce": 76853299,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "aH3qXnAfHNMcsOWqjBFCy",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "ixOzTW7m"
				},
				{
					"id": "r1bAz843HHjfvNZSxFWDw",
					"type": "arrow"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "ixOzTW7m",
			"type": "text",
			"x": -701.9750429789228,
			"y": 314.2213477847798,
			"width": 77.99993896484375,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 802438771,
			"version": 298,
			"versionNonce": 429273555,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "첫번째\ncmd인가?",
			"rawText": "첫번째 cmd인가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "5pQRl2SNRgr3eUBGu9Jsu",
			"originalText": "첫번째 cmd인가?",
			"lineHeight": 1.25
		},
		{
			"id": "KAeY3cInEHa3aGauhJnkr",
			"type": "arrow",
			"x": -751.2421175638838,
			"y": 338.6311530826314,
			"width": 134.84895636232454,
			"height": 3.4639594621563674,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 118234141,
			"version": 868,
			"versionNonce": 1862415122,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "ImKQfSgh"
				}
			],
			"updated": 1718685323647,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-134.84895636232454,
					-3.4639594621563674
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 8.354631611981617,
				"focus": -0.06476476588950862
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "ImKQfSgh",
			"type": "text",
			"x": -441.1150321960449,
			"y": 337.8748461164854,
			"width": 31.179962158203125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1598263773,
			"version": 20,
			"versionNonce": 791652307,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "yes",
			"rawText": "yes",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "KAeY3cInEHa3aGauhJnkr",
			"originalText": "yes",
			"lineHeight": 1.25
		},
		{
			"id": "r1bAz843HHjfvNZSxFWDw",
			"type": "arrow",
			"x": -665.7258516947431,
			"y": 422.68541333653764,
			"width": 2.536663766087713,
			"height": 117.13782649152643,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1080065213,
			"version": 945,
			"versionNonce": 861989842,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "NtthsPTB"
				}
			],
			"updated": 1718685323646,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					2.536663766087713,
					117.13782649152643
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "5pQRl2SNRgr3eUBGu9Jsu",
				"gap": 2.1669156246953136,
				"focus": 0.04862497263445719
			},
			"endBinding": {
				"elementId": "QU5pfgVPZvgNlKLv02Fuh",
				"gap": 7.136067849058136,
				"focus": 0.028712669411705898
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "NtthsPTB",
			"type": "text",
			"x": -285.1574058532715,
			"y": 478.4426866926573,
			"width": 20.41998291015625,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 2048282963,
			"version": 9,
			"versionNonce": 288437619,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "no",
			"rawText": "no",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "r1bAz843HHjfvNZSxFWDw",
			"originalText": "no",
			"lineHeight": 1.25
		},
		{
			"id": "fiM2lTLJTs5SjZrAZ9Omg",
			"type": "arrow",
			"x": 142.80459330189407,
			"y": 151.9439888162538,
			"width": 112.2286899317485,
			"height": 103.53227814542151,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 959484115,
			"version": 147,
			"versionNonce": 1543263954,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "SRPVMbzL"
				}
			],
			"updated": 1718685323644,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					105.47728612315476,
					5.636343086827765
				],
				[
					112.2286899317485,
					103.53227814542151
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"gap": 1,
				"focus": -0.1556077246926263
			},
			"endBinding": {
				"elementId": "1W6O_eTj_WMBE3oe4sMOc",
				"gap": 7.581562553247579,
				"focus": 0.03678485214672037
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "SRPVMbzL",
			"type": "text",
			"x": 227.8018913269043,
			"y": 145.08033190308157,
			"width": 40.95997619628906,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1227292797,
			"version": 10,
			"versionNonce": 49286931,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "SEM",
			"rawText": "SEM",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "fiM2lTLJTs5SjZrAZ9Omg",
			"originalText": "SEM",
			"lineHeight": 1.25
		},
		{
			"id": "Ey1jaK3BNLMCEc0sgH_A6",
			"type": "arrow",
			"x": -1126.1160288825195,
			"y": 337.8110130164707,
			"width": 105.00442273209569,
			"height": 1.7642812500297964,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 981251453,
			"version": 1148,
			"versionNonce": 679034258,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "XYYrdpbF"
				}
			],
			"updated": 1718685323648,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-105.00442273209569,
					1.7642812500297964
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 1,
				"focus": 0.024167169808285236
			},
			"endBinding": {
				"elementId": "F-cf99_OFLVwhbVBTtAjk",
				"gap": 5.940086359424868,
				"focus": 0.0778221828932911
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "XYYrdpbF",
			"type": "text",
			"x": -801.7094230651855,
			"y": 340.0736092159468,
			"width": 31.179962158203125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1566132819,
			"version": 16,
			"versionNonce": 920827059,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "yes",
			"rawText": "yes",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "Ey1jaK3BNLMCEc0sgH_A6",
			"originalText": "yes",
			"lineHeight": 1.25
		},
		{
			"id": "1W6O_eTj_WMBE3oe4sMOc",
			"type": "rectangle",
			"x": 175.22542190551758,
			"y": 263.0578295149229,
			"width": 162.42388916015625,
			"height": 116.4742431640625,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1121942493,
			"version": 75,
			"versionNonce": 1287674365,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "fiM2lTLJTs5SjZrAZ9Omg",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "CGSCc1Tz"
				},
				{
					"id": "W-gbpyKASOZ5I7x8dF7Ac",
					"type": "arrow"
				}
			],
			"updated": 1718677383686,
			"link": null,
			"locked": false
		},
		{
			"id": "CGSCc1Tz",
			"type": "text",
			"x": 183.01742935180664,
			"y": 271.29495109695415,
			"width": 146.83987426757812,
			"height": 100,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 839427805,
			"version": 80,
			"versionNonce": 1286579795,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "wait_child_end\n후 child_num,\nfirst_cmd를\n원상복구",
			"rawText": "wait_child_end 후 child_num, first_cmd를 원상복구",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 92,
			"containerId": "1W6O_eTj_WMBE3oe4sMOc",
			"originalText": "wait_child_end 후 child_num, first_cmd를 원상복구",
			"lineHeight": 1.25
		},
		{
			"id": "cND-KRhE_XOx2i9nk6aZa",
			"type": "arrow",
			"x": -1008.5575472513839,
			"y": 433.6274530732835,
			"width": 2.2927962242262083,
			"height": 110.51907764062844,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 540197875,
			"version": 777,
			"versionNonce": 2083461650,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "Mw7TQbMl"
				}
			],
			"updated": 1718685323647,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					2.2927962242262083,
					110.51907764062844
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 1.005451874344402,
				"focus": 0.008674823656158898
			},
			"endBinding": {
				"elementId": "6hHfwv__MFMv-8IHEmJPG",
				"gap": 2.7010688195248633,
				"focus": 0.03077927044010694
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "Mw7TQbMl",
			"type": "text",
			"x": -628.0663871765137,
			"y": 488.1233128551844,
			"width": 20.41998291015625,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 2127912061,
			"version": 17,
			"versionNonce": 724394995,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "no",
			"rawText": "no",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "cND-KRhE_XOx2i9nk6aZa",
			"originalText": "no",
			"lineHeight": 1.25
		},
		{
			"id": "6hHfwv__MFMv-8IHEmJPG",
			"type": "diamond",
			"x": -1113.2078768412275,
			"y": 546.6398432100023,
			"width": 211.80859375,
			"height": 209.1134033203125,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 306785843,
			"version": 406,
			"versionNonce": 1082854707,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "cND-KRhE_XOx2i9nk6aZa",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "KxjWML7L"
				},
				{
					"id": "euRjN5ag-K66kdfpKSvV4",
					"type": "arrow"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "KxjWML7L",
			"type": "text",
			"x": -1039.9257036844892,
			"y": 626.4181940400804,
			"width": 65.33995056152344,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 953854387,
			"version": 292,
			"versionNonce": 548990675,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "cmd가\ncd인가?",
			"rawText": "cmd가 cd인가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "6hHfwv__MFMv-8IHEmJPG",
			"originalText": "cmd가 cd인가?",
			"lineHeight": 1.25
		},
		{
			"id": "pjM6GJmMpyEdYQO-C-uHb",
			"type": "arrow",
			"x": -1110.9702974955244,
			"y": 650.0539667451585,
			"width": 112.85783386230469,
			"height": 0.45465087890625,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1012184637,
			"version": 611,
			"versionNonce": 435523922,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "MDrJZHS7"
				}
			],
			"updated": 1718685323645,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-112.85783386230469,
					0.45465087890625
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "AtGFDHk6sDbRnxbXe5tHJ",
				"gap": 2.3178558349609375,
				"focus": -0.07667268804142063
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "MDrJZHS7",
			"type": "text",
			"x": -793.4276313781738,
			"y": 649.8459080700281,
			"width": 31.179962158203125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1237998483,
			"version": 14,
			"versionNonce": 495272755,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "yes",
			"rawText": "yes",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "pjM6GJmMpyEdYQO-C-uHb",
			"originalText": "yes",
			"lineHeight": 1.25
		},
		{
			"id": "AtGFDHk6sDbRnxbXe5tHJ",
			"type": "rectangle",
			"x": -1379.5629717508955,
			"y": 588.1053278291429,
			"width": 153.41698455810547,
			"height": 135.911376953125,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 633988925,
			"version": 390,
			"versionNonce": 400387411,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "pjM6GJmMpyEdYQO-C-uHb",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "ZN1naXKl"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "ZN1naXKl",
			"type": "text",
			"x": -1354.634440104167,
			"y": 643.5610163057054,
			"width": 103.55992126464844,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1888722461,
			"version": 280,
			"versionNonce": 2064272115,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "ft_cd 실행",
			"rawText": "ft_cd 실행",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "AtGFDHk6sDbRnxbXe5tHJ",
			"originalText": "ft_cd 실행",
			"lineHeight": 1.25
		},
		{
			"id": "euRjN5ag-K66kdfpKSvV4",
			"type": "arrow",
			"x": -1004.1155237479966,
			"y": 755.5421835701212,
			"width": 1.701302449515424,
			"height": 84.33501787177522,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 713218515,
			"version": 953,
			"versionNonce": 313162386,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "yNlahHJ6"
				}
			],
			"updated": 1718685323645,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					1.701302449515424,
					84.33501787177522
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "6hHfwv__MFMv-8IHEmJPG",
				"gap": 2.089619262817436,
				"focus": -0.010226937599431355
			},
			"endBinding": {
				"elementId": "-NzEpyPXQaCDKgdYZB2En",
				"gap": 7.537068146611972,
				"focus": 0.005008309829804068
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "yNlahHJ6",
			"type": "text",
			"x": -624.5094261169434,
			"y": 810.50310411495,
			"width": 20.41998291015625,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 305207709,
			"version": 13,
			"versionNonce": 1885229683,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "no",
			"rawText": "no",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "euRjN5ag-K66kdfpKSvV4",
			"originalText": "no",
			"lineHeight": 1.25
		},
		{
			"id": "-NzEpyPXQaCDKgdYZB2En",
			"type": "diamond",
			"x": -1126.9841524759931,
			"y": 847.0757278914953,
			"width": 253.60690307617185,
			"height": 270,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1081996733,
			"version": 430,
			"versionNonce": 1134270226,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "euRjN5ag-K66kdfpKSvV4",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "MJH5dMK2"
				}
			],
			"updated": 1718685323645,
			"link": null,
			"locked": false
		},
		{
			"id": "MJH5dMK2",
			"type": "text",
			"x": -1051.9823900858564,
			"y": 944.5757278914953,
			"width": 103.7999267578125,
			"height": 75,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1937668413,
			"version": 441,
			"versionNonce": 1080121426,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323646,
			"link": null,
			"locked": false,
			"text": "자식\n프로세스에서\ncmd 실행",
			"rawText": "자식 프로세스에서 cmd 실행",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 67,
			"containerId": "-NzEpyPXQaCDKgdYZB2En",
			"originalText": "자식 프로세스에서 cmd 실행",
			"lineHeight": 1.25
		},
		{
			"id": "QU5pfgVPZvgNlKLv02Fuh",
			"type": "diamond",
			"x": -759.534881955101,
			"y": 546.9260396278426,
			"width": 191.31487165178578,
			"height": 175.8924211774555,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 896966301,
			"version": 370,
			"versionNonce": 1576024243,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "r1bAz843HHjfvNZSxFWDw",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "yGrokf01"
				},
				{
					"id": "qNyuN6fe3bbGG36SjGCw5",
					"type": "arrow"
				},
				{
					"id": "xG5ChkiI0VgzWRksyNk9I",
					"type": "arrow"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "yGrokf01",
			"type": "text",
			"x": -702.7061335245764,
			"y": 609.8991449222065,
			"width": 77.99993896484375,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1236084957,
			"version": 292,
			"versionNonce": 1064086099,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "마지막\ncmd인가?",
			"rawText": "마지막 cmd인가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "QU5pfgVPZvgNlKLv02Fuh",
			"originalText": "마지막 cmd인가?",
			"lineHeight": 1.25
		},
		{
			"id": "qNyuN6fe3bbGG36SjGCw5",
			"type": "arrow",
			"x": -661.0867697089363,
			"y": 723.0892097233249,
			"width": 4.510048552528588,
			"height": 96.59025659257611,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 384398557,
			"version": 1024,
			"versionNonce": 699363218,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "T7v2dtmS"
				}
			],
			"updated": 1718685323647,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					4.510048552528588,
					96.59025659257611
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "QU5pfgVPZvgNlKLv02Fuh",
				"gap": 2.0880770181181276,
				"focus": 0.013887067465206956
			},
			"endBinding": {
				"elementId": "r8R_jPiyqoEbtxbybRZ4u",
				"gap": 17.689685527555127,
				"focus": 0.016809374373315453
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "T7v2dtmS",
			"type": "text",
			"x": -325.5337916782917,
			"y": 774.8315891767637,
			"width": 107.97990417480469,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 539827731,
			"version": 26,
			"versionNonce": 1135993683,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "no(mid cmd)",
			"rawText": "no(mid cmd)",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "qNyuN6fe3bbGG36SjGCw5",
			"originalText": "no(mid cmd)",
			"lineHeight": 1.25
		},
		{
			"id": "xG5ChkiI0VgzWRksyNk9I",
			"type": "arrow",
			"x": -563.7074577360513,
			"y": 632.1499085520184,
			"width": 116.09553197514697,
			"height": 1.1109277271890505,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 672557373,
			"version": 608,
			"versionNonce": 874931794,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "tLIPMmca"
				}
			],
			"updated": 1718685323646,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					116.09553197514697,
					-1.1109277271890505
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "QU5pfgVPZvgNlKLv02Fuh",
				"gap": 5.270130435850305,
				"focus": -0.02005551764510863
			},
			"endBinding": {
				"elementId": "k1kIAIBmMZrOU4rvo3Diw",
				"gap": 13.414655412946331,
				"focus": 0.031828199326164555
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "tLIPMmca",
			"type": "text",
			"x": -116.61578478131895,
			"y": 631.6245404881477,
			"width": 31.179962158203125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1679204435,
			"version": 14,
			"versionNonce": 1080295667,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677269129,
			"link": null,
			"locked": false,
			"text": "yes",
			"rawText": "yes",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "xG5ChkiI0VgzWRksyNk9I",
			"originalText": "yes",
			"lineHeight": 1.25
		},
		{
			"id": "k1kIAIBmMZrOU4rvo3Diw",
			"type": "rectangle",
			"x": -434.197270347958,
			"y": 548.0343914500406,
			"width": 214.2681884765626,
			"height": 169.15113176618308,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 2017457245,
			"version": 320,
			"versionNonce": 1658106141,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "u61wo1qW"
				},
				{
					"id": "xG5ChkiI0VgzWRksyNk9I",
					"type": "arrow"
				}
			],
			"updated": 1718677313941,
			"link": null,
			"locked": false
		},
		{
			"id": "u61wo1qW",
			"type": "text",
			"x": -428.1031159900478,
			"y": 582.6099573331321,
			"width": 202.0798797607422,
			"height": 100,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1372140317,
			"version": 423,
			"versionNonce": 1467356595,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로\nredirection, cmd를\n실행",
			"rawText": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로 redirection, cmd를 실행",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 92,
			"containerId": "k1kIAIBmMZrOU4rvo3Diw",
			"originalText": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로 redirection, cmd를 실행",
			"lineHeight": 1.25
		},
		{
			"id": "r8R_jPiyqoEbtxbybRZ4u",
			"type": "rectangle",
			"x": -822.4985747564403,
			"y": 837.3691518434562,
			"width": 335.50885881696433,
			"height": 166.7016601562501,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1832187229,
			"version": 456,
			"versionNonce": 1793707026,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "qNyuN6fe3bbGG36SjGCw5",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "gbvsKCeG"
				}
			],
			"updated": 1718685323646,
			"link": null,
			"locked": false
		},
		{
			"id": "gbvsKCeG",
			"type": "text",
			"x": -792.2240342639739,
			"y": 870.7199819215812,
			"width": 274.95977783203125,
			"height": 100,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1984961149,
			"version": 683,
			"versionNonce": 1962913106,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323647,
			"link": null,
			"locked": false,
			"text": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을\nredirection, 두번째 pipe로 표준\n출력을 redirection, cmd를 실행",
			"rawText": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을 redirection, 두번째 pipe로 표준 출력을 redirection, cmd를 실행",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 92,
			"containerId": "r8R_jPiyqoEbtxbybRZ4u",
			"originalText": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을 redirection, 두번째 pipe로 표준 출력을 redirection, cmd를 실행",
			"lineHeight": 1.25
		},
		{
			"id": "1tVAwC5j9kiE558cU_ghJ",
			"type": "diamond",
			"x": -1125.1743990580244,
			"y": 243.16600415685014,
			"width": 231.27841186523435,
			"height": 189.96331787109375,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1100740371,
			"version": 530,
			"versionNonce": 1021322291,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "KAeY3cInEHa3aGauhJnkr",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "3ghEIm5q"
				},
				{
					"id": "Ey1jaK3BNLMCEc0sgH_A6",
					"type": "arrow"
				},
				{
					"id": "cND-KRhE_XOx2i9nk6aZa",
					"type": "arrow"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "3ghEIm5q",
			"type": "text",
			"x": -1057.2647616068525,
			"y": 300.6568336246236,
			"width": 95.81993103027344,
			"height": 75,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 910200819,
			"version": 557,
			"versionNonce": 542320083,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "cmd 뒤에\nPIPE가\n존재하는가?",
			"rawText": "cmd 뒤에  PIPE가 \n존재하는가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 67,
			"containerId": "1tVAwC5j9kiE558cU_ghJ",
			"originalText": "cmd 뒤에  PIPE가 \n존재하는가?",
			"lineHeight": 1.25
		},
		{
			"id": "F-cf99_OFLVwhbVBTtAjk",
			"type": "rectangle",
			"x": -1556.669394175212,
			"y": 251.9735929399053,
			"width": 319.6088562011719,
			"height": 167.33294677734372,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1750770077,
			"version": 386,
			"versionNonce": 690234451,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "Ey1jaK3BNLMCEc0sgH_A6",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "xhAb0NSv"
				}
			],
			"updated": 1718677313275,
			"link": null,
			"locked": false
		},
		{
			"id": "xhAb0NSv",
			"type": "text",
			"x": -1543.974859873454,
			"y": 285.6400663285772,
			"width": 294.21978759765625,
			"height": 100,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 697722429,
			"version": 638,
			"versionNonce": 1080173043,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677313275,
			"link": null,
			"locked": false,
			"text": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의\nWRITE로 redirection, execve로\ncmd를 실행한다.",
			"rawText": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의 WRITE로 redirection, execve로 cmd를 실행한다. ",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 92,
			"containerId": "F-cf99_OFLVwhbVBTtAjk",
			"originalText": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의 WRITE로 redirection, execve로 cmd를 실행한다. ",
			"lineHeight": 1.25
		},
		{
			"id": "nE6mSUKFTnqDgAAPee_iA",
			"type": "rectangle",
			"x": -1580.5640624515581,
			"y": 184.6321403401979,
			"width": 1378.1947157118066,
			"height": 914.7397189670146,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "dotted",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1362570579,
			"version": 171,
			"versionNonce": 937970931,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "Ey1jaK3BNLMCEc0sgH_A6",
					"type": "arrow"
				},
				{
					"id": "PfjOWXmkROGl-mRaXlo_X",
					"type": "arrow"
				}
			],
			"updated": 1718677391495,
			"link": null,
			"locked": false
		},
		{
			"id": "EU1enNzAFnkDWZEu8g_CW",
			"type": "rectangle",
			"x": -117.51422046479433,
			"y": 506.949950398792,
			"width": 251.86503092447947,
			"height": 127.94989691840283,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"seed": 1548453277,
			"version": 156,
			"versionNonce": 1432337234,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "ImpBiiGL"
				},
				{
					"id": "4HDKNULTh5shvcL1dblCx",
					"type": "arrow"
				},
				{
					"id": "W-gbpyKASOZ5I7x8dF7Ac",
					"type": "arrow"
				}
			],
			"updated": 1718685323648,
			"link": null,
			"locked": false
		},
		{
			"id": "ImpBiiGL",
			"type": "text",
			"x": -80.88162413097257,
			"y": 558.4248988579934,
			"width": 178.59983825683594,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1787804509,
			"version": 156,
			"versionNonce": 405585373,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677377008,
			"link": null,
			"locked": false,
			"text": "go_to_next_node",
			"rawText": "go_to_next_node",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "EU1enNzAFnkDWZEu8g_CW",
			"originalText": "go_to_next_node",
			"lineHeight": 1.25
		},
		{
			"id": "W-gbpyKASOZ5I7x8dF7Ac",
			"type": "arrow",
			"x": 263.39689878433785,
			"y": 387.6309671088612,
			"width": 120.34261067708348,
			"height": 187.29566786024327,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 954370067,
			"version": 82,
			"versionNonce": 244114578,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323648,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-4.9593098958332575,
					166.19079589843773
				],
				[
					-120.34261067708348,
					187.29566786024327
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "1W6O_eTj_WMBE3oe4sMOc",
				"gap": 8.098894429875827,
				"focus": -0.107764807797704
			},
			"endBinding": {
				"elementId": "EU1enNzAFnkDWZEu8g_CW",
				"gap": 8.70347764756923,
				"focus": 0.3290235408885383
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "PfjOWXmkROGl-mRaXlo_X",
			"type": "arrow",
			"x": -198.71111987885695,
			"y": 561.4752325168475,
			"width": 83.23744032118066,
			"height": 1.5848795572916288,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 953839965,
			"version": 49,
			"versionNonce": 148090707,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677391495,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					83.23744032118066,
					1.5848795572916288
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "nE6mSUKFTnqDgAAPee_iA",
				"focus": -0.19919028555638266,
				"gap": 3.658226860894615
			},
			"endBinding": null,
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "hI0YGZHEp9mp499lYt_-U",
			"type": "arrow",
			"x": 3.7660936628089985,
			"y": 633.8369610408134,
			"width": 2.641426444317415,
			"height": 69.07004451137789,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1295325405,
			"version": 240,
			"versionNonce": 677806674,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718685323648,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					2.641426444317415,
					69.07004451137789
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "LDW3KJHpj9ZHQb80AnUp3",
				"gap": 5.733155307528932,
				"focus": 0.010209091487069551
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "LDW3KJHpj9ZHQb80AnUp3",
			"type": "diamond",
			"x": -171.9866732642745,
			"y": 708.4632902508831,
			"width": 359.61452907986154,
			"height": 158.78851996527786,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 857934835,
			"version": 261,
			"versionNonce": 100824765,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "hI0YGZHEp9mp499lYt_-U",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "mvIk1Ww6"
				},
				{
					"id": "N2VeoGExp6ra7tzslX25q",
					"type": "arrow"
				}
			],
			"updated": 1718677447280,
			"link": null,
			"locked": false
		},
		{
			"id": "mvIk1Ww6",
			"type": "text",
			"x": -73.99296836247316,
			"y": 762.6604202422026,
			"width": 163.81985473632812,
			"height": 50,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 256595933,
			"version": 141,
			"versionNonce": 1791326579,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677441629,
			"link": null,
			"locked": false,
			"text": "parse_list의 끝에\n도달하였는가?",
			"rawText": "parse_list의 끝에 도달하였는가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "LDW3KJHpj9ZHQb80AnUp3",
			"originalText": "parse_list의 끝에 도달하였는가?",
			"lineHeight": 1.25
		},
		{
			"id": "N2VeoGExp6ra7tzslX25q",
			"type": "arrow",
			"x": 185.55921762346634,
			"y": 785.8509928691811,
			"width": 341.83730993534357,
			"height": 822.556506801307,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1442474579,
			"version": 83,
			"versionNonce": 415655954,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "x9B0h64y"
				}
			],
			"updated": 1718685323648,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					318.965203947329,
					-451.87337970163173
				],
				[
					-22.872105988014596,
					-822.556506801307
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "LDW3KJHpj9ZHQb80AnUp3",
				"gap": 1,
				"focus": 0.980618064545895
			},
			"endBinding": {
				"elementId": "eMRLaDVmsHbOypzWeesJz",
				"gap": 1.8871363771649925,
				"focus": -0.9774052400379022
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "x9B0h64y",
			"type": "text",
			"x": 494.3144301157172,
			"y": 321.4776131675494,
			"width": 20.41998291015625,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1323219059,
			"version": 7,
			"versionNonce": 915149533,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677458014,
			"link": null,
			"locked": false,
			"text": "no",
			"rawText": "no",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "N2VeoGExp6ra7tzslX25q",
			"originalText": "no",
			"lineHeight": 1.25
		},
		{
			"id": "q2WUslEi7sCGPsa92msa9",
			"type": "arrow",
			"x": 5.562290494405943,
			"y": 865.970411019112,
			"width": 0.5463876183309191,
			"height": 106.06793720269297,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 1583502515,
			"version": 201,
			"versionNonce": 1201903058,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "8Knk1zfn"
				}
			],
			"updated": 1718685323649,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-0.5463876183309191,
					106.06793720269297
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "0dtl-WH2-sD19VTITHJs8",
				"gap": 21.220397949218807,
				"focus": 0.0441515337609202
			},
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "8Knk1zfn",
			"type": "text",
			"x": -8.723504929313663,
			"y": 903.3831646540948,
			"width": 31.179962158203125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 1619307229,
			"version": 8,
			"versionNonce": 599448179,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677475652,
			"link": null,
			"locked": false,
			"text": "yes",
			"rawText": "yes",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "q2WUslEi7sCGPsa92msa9",
			"originalText": "yes",
			"lineHeight": 1.25
		},
		{
			"id": "0dtl-WH2-sD19VTITHJs8",
			"type": "ellipse",
			"x": -99.01093812972613,
			"y": 993.2004321779666,
			"width": 198.5216606987849,
			"height": 106.56100802951417,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"seed": 903270141,
			"version": 207,
			"versionNonce": 1512796563,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "q2WUslEi7sCGPsa92msa9",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "NUXNTJc4"
				}
			],
			"updated": 1718677492532,
			"link": null,
			"locked": false
		},
		{
			"id": "NUXNTJc4",
			"type": "text",
			"x": -15.768100598862162,
			"y": 1033.805930498852,
			"width": 31.65997314453125,
			"height": 25,
			"angle": 0,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"seed": 829555901,
			"version": 6,
			"versionNonce": 32237395,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718677494747,
			"link": null,
			"locked": false,
			"text": "end",
			"rawText": "end",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 17,
			"containerId": "0dtl-WH2-sD19VTITHJs8",
			"originalText": "end",
			"lineHeight": 1.25
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1e1e1e",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "solid",
		"currentItemStrokeWidth": 2,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 1,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"scrollX": 2178.3282005673364,
		"scrollY": 763.2719983018867,
		"zoom": {
			"value": 0.4499999999999996
		},
		"currentItemRoundness": "round",
		"gridSize": null,
		"gridColor": {
			"Bold": "#C9C9C9FF",
			"Regular": "#EDEDEDFF"
		},
		"currentStrokeOptions": null,
		"previousGridSize": null,
		"frameRendering": {
			"enabled": true,
			"clip": true,
			"name": true,
			"outline": true
		}
	},
	"files": {}
}
```
%%