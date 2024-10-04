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
			"type": "ellipse",
			"version": 251,
			"versionNonce": 636800014,
			"isDeleted": false,
			"id": "eCJMh6R5",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -139.38215255737305,
			"y": -414.77381896972656,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 268.2359924316406,
			"height": 156,
			"seed": 1104327123,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280905,
			"link": "[[parse_line-flowchart.excalidraw]]",
			"locked": false
		},
		{
			"type": "text",
			"version": 305,
			"versionNonce": 2040021970,
			"isDeleted": false,
			"id": "TdAlpDw3",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -89.71982739754773,
			"y": -386.92814790227726,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 169.23985290527344,
			"height": 100,
			"seed": 1442734803,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280905,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "start\nparse_line으로부터\nparse_list를\n넘겨받는다.",
			"rawText": "start\nparse_line으로부터 parse_list를 넘겨받는다.",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "eCJMh6R5",
			"originalText": "start\nparse_line으로부터 parse_list를 넘겨받는다.",
			"lineHeight": 1.25,
			"baseline": 93
		},
		{
			"type": "arrow",
			"version": 176,
			"versionNonce": 1037834830,
			"isDeleted": false,
			"id": "9SRhzMqmd_vlpfAC2_VK_",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -4.250432650831772,
			"y": -253.5864140735398,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 1.2298121398438413,
			"height": 31.56460715083614,
			"seed": 1428277011,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1728023280905,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-1.2298121398438413,
					31.56460715083614
				]
			]
		},
		{
			"type": "rectangle",
			"version": 177,
			"versionNonce": 826538386,
			"isDeleted": false,
			"id": "yyJ8PnOt1EVY-tsv5AtgY",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -128.9133415222168,
			"y": -209.34797879770366,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 243.53030395507812,
			"height": 62.75390625,
			"seed": 1302951859,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280905,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 146,
			"versionNonce": 1883218062,
			"isDeleted": false,
			"id": "CpOgMOAQ",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -105.32809066772461,
			"y": -202.97102567270366,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 196.35980224609375,
			"height": 50,
			"seed": 1320650003,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "pipe_fd, pipe_fd_2,\nfirst_cmd를 초기화",
			"rawText": "pipe_fd, pipe_fd_2, first_cmd를 초기화",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "yyJ8PnOt1EVY-tsv5AtgY",
			"originalText": "pipe_fd, pipe_fd_2, first_cmd를 초기화",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 767,
			"versionNonce": 1836250962,
			"isDeleted": false,
			"id": "cFyqHOnf8HhtEl1cSmIhP",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -5.328349783485435,
			"y": -145.59407254770366,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 1.808730838205661,
			"height": 39.226367650681794,
			"seed": 228947091,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					1.808730838205661,
					39.226367650681794
				]
			]
		},
		{
			"type": "diamond",
			"version": 514,
			"versionNonce": 282615502,
			"isDeleted": false,
			"id": "eMRLaDVmsHbOypzWeesJz",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -185.35854721069336,
			"y": -99.25081082895366,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 349.64854431152344,
			"height": 120,
			"seed": 819178653,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 597,
			"versionNonce": 1316764946,
			"isDeleted": false,
			"id": "aQAwrp0Y",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -29.086387634277344,
			"y": -51.75081082895366,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 37.27995300292969,
			"height": 25,
			"seed": 1302912157,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "loop",
			"rawText": "loop",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "eMRLaDVmsHbOypzWeesJz",
			"originalText": "loop",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 157,
			"versionNonce": 339694862,
			"isDeleted": false,
			"id": "8Mxo_eQ0Nam1UPacnFzWk",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -7.00263897220577,
			"y": 26.06312406516105,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.022555945500537966,
			"height": 55.35664415641773,
			"seed": 1062958653,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "1mwFaf2j"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-0.022555945500537966,
					55.35664415641773
				]
			]
		},
		{
			"type": "text",
			"version": 14,
			"versionNonce": 1373031122,
			"isDeleted": false,
			"id": "1mwFaf2j",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -17.126354217529297,
			"y": 47.40434053823384,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 1151589875,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "8Mxo_eQ0Nam1UPacnFzWk",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "diamond",
			"version": 173,
			"versionNonce": 1944945486,
			"isDeleted": false,
			"id": "N0bwk0I_LBNWpL3Pkpm_P",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -157.6782341003418,
			"y": 91.85181627808157,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 301.7703552246094,
			"height": 123.3980712890625,
			"seed": 540203987,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 96,
			"versionNonce": 773431442,
			"isDeleted": false,
			"id": "OyqaaS8l",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -71.14558792114258,
			"y": 128.7013341003472,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 128.81988525390625,
			"height": 50,
			"seed": 1221859603,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "node의 type이\n무엇인가?",
			"rawText": "node의 type이 무엇인가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "N0bwk0I_LBNWpL3Pkpm_P",
			"originalText": "node의 type이 무엇인가?",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 624,
			"versionNonce": 305916302,
			"isDeleted": false,
			"id": "aH3qXnAfHNMcsOWqjBFCy",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -156.53715133666987,
			"y": 157.46448717651907,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 441.29800733983456,
			"height": 148.1502550365247,
			"seed": 356529331,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "YfcFH3Vm"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
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
			]
		},
		{
			"type": "text",
			"version": 22,
			"versionNonce": 788250194,
			"isDeleted": false,
			"id": "YfcFH3Vm",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -284.4603157043457,
			"y": 153.34430895386282,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 43.79997253417969,
			"height": 25,
			"seed": 1171712691,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "CMD",
			"rawText": "CMD",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "aH3qXnAfHNMcsOWqjBFCy",
			"originalText": "CMD",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 79,
			"versionNonce": 509839310,
			"isDeleted": false,
			"id": "4HDKNULTh5shvcL1dblCx",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -3.5124320983886714,
			"y": 217.44294176636285,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.834485516793078,
			"height": 267.69310538396985,
			"seed": 198189693,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "kDdUqVXE"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					0.834485516793078,
					267.69310538396985
				]
			]
		},
		{
			"type": "text",
			"version": 11,
			"versionNonce": 290726930,
			"isDeleted": false,
			"id": "kDdUqVXE",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -28.91348648071289,
			"y": 244.5600987487847,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 50.81996154785156,
			"height": 25,
			"seed": 1652306739,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "PIPE",
			"rawText": "PIPE",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "4HDKNULTh5shvcL1dblCx",
			"originalText": "PIPE",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 151,
			"versionNonce": 2021481998,
			"isDeleted": false,
			"id": "fiM2lTLJTs5SjZrAZ9Omg",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 142.80459330189407,
			"y": 151.9439888162538,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 112.2286899317485,
			"height": 103.53227814542151,
			"seed": 959484115,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "SRPVMbzL"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
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
			]
		},
		{
			"type": "text",
			"version": 12,
			"versionNonce": 1595527634,
			"isDeleted": false,
			"id": "SRPVMbzL",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 227.8018913269043,
			"y": 145.08033190308157,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 40.95997619628906,
			"height": 25,
			"seed": 1227292797,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "SEM",
			"rawText": "SEM",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "fiM2lTLJTs5SjZrAZ9Omg",
			"originalText": "SEM",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 77,
			"versionNonce": 360868942,
			"isDeleted": false,
			"id": "1W6O_eTj_WMBE3oe4sMOc",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 175.22542190551758,
			"y": 263.0578295149229,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 162.42388916015625,
			"height": 116.4742431640625,
			"seed": 1121942493,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 82,
			"versionNonce": 1264830354,
			"isDeleted": false,
			"id": "CGSCc1Tz",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 183.01742935180664,
			"y": 271.29495109695415,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 146.83987426757812,
			"height": 100,
			"seed": 839427805,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "wait_child_end\n후 child_num,\nfirst_cmd를\n원상복구",
			"rawText": "wait_child_end 후 child_num, first_cmd를 원상복구",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "1W6O_eTj_WMBE3oe4sMOc",
			"originalText": "wait_child_end 후 child_num, first_cmd를 원상복구",
			"lineHeight": 1.25,
			"baseline": 93
		},
		{
			"type": "diamond",
			"version": 482,
			"versionNonce": 1665905294,
			"isDeleted": false,
			"id": "5pQRl2SNRgr3eUBGu9Jsu",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -752.77245203654,
			"y": 256.26475903966264,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 179.18951416015625,
			"height": 165.82635498046875,
			"seed": 1696028157,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 376,
			"versionNonce": 241763666,
			"isDeleted": false,
			"id": "ixOzTW7m",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -701.9750429789228,
			"y": 314.2213477847798,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 77.99993896484375,
			"height": 50,
			"seed": 802438771,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "첫번째\ncmd인가?",
			"rawText": "첫번째 cmd인가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "5pQRl2SNRgr3eUBGu9Jsu",
			"originalText": "첫번째 cmd인가?",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 1023,
			"versionNonce": 747778254,
			"isDeleted": false,
			"id": "KAeY3cInEHa3aGauhJnkr",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -751.2421175638838,
			"y": 338.6311530826314,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 134.84895636232454,
			"height": 3.4639594621563674,
			"seed": 118234141,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "ImKQfSgh"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 8.354631611981617,
				"focus": -0.06476476588950862
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-134.84895636232454,
					-3.4639594621563674
				]
			]
		},
		{
			"type": "text",
			"version": 98,
			"versionNonce": 1098943250,
			"isDeleted": false,
			"id": "ImKQfSgh",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -441.1150321960449,
			"y": 337.8748461164854,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1598263773,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "KAeY3cInEHa3aGauhJnkr",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 1179,
			"versionNonce": 2096031502,
			"isDeleted": false,
			"id": "r1bAz843HHjfvNZSxFWDw",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -665.7258516947431,
			"y": 422.68541333653764,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 2.536663766087713,
			"height": 117.13782649152643,
			"seed": 1080065213,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "NtthsPTB"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					2.536663766087713,
					117.13782649152643
				]
			]
		},
		{
			"type": "text",
			"version": 87,
			"versionNonce": 992041170,
			"isDeleted": false,
			"id": "NtthsPTB",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -285.1574058532715,
			"y": 478.4426866926573,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 2048282963,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "r1bAz843HHjfvNZSxFWDw",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 1382,
			"versionNonce": 81450318,
			"isDeleted": false,
			"id": "Ey1jaK3BNLMCEc0sgH_A6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1126.1160288825195,
			"y": 337.8110130164707,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 105.00442273209569,
			"height": 1.7642812500297964,
			"seed": 981251453,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "XYYrdpbF"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-105.00442273209569,
					1.7642812500297964
				]
			]
		},
		{
			"type": "text",
			"version": 94,
			"versionNonce": 1793224338,
			"isDeleted": false,
			"id": "XYYrdpbF",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -801.7094230651855,
			"y": 340.0736092159468,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1566132819,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "Ey1jaK3BNLMCEc0sgH_A6",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 1011,
			"versionNonce": 2108619662,
			"isDeleted": false,
			"id": "cND-KRhE_XOx2i9nk6aZa",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1008.5575472513839,
			"y": 433.6274530732835,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 2.2927962242262083,
			"height": 110.51907764062844,
			"seed": 540197875,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "Mw7TQbMl"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					2.2927962242262083,
					110.51907764062844
				]
			]
		},
		{
			"type": "text",
			"version": 95,
			"versionNonce": 897240146,
			"isDeleted": false,
			"id": "Mw7TQbMl",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -628.0663871765137,
			"y": 488.1233128551844,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 2127912061,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "cND-KRhE_XOx2i9nk6aZa",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "diamond",
			"version": 484,
			"versionNonce": 228874702,
			"isDeleted": false,
			"id": "6hHfwv__MFMv-8IHEmJPG",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1113.2078768412275,
			"y": 546.6398432100023,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 211.80859375,
			"height": 209.1134033203125,
			"seed": 306785843,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 370,
			"versionNonce": 1354854930,
			"isDeleted": false,
			"id": "KxjWML7L",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1039.9257036844892,
			"y": 626.4181940400804,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 65.33995056152344,
			"height": 50,
			"seed": 953854387,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "cmd가\ncd인가?",
			"rawText": "cmd가 cd인가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "6hHfwv__MFMv-8IHEmJPG",
			"originalText": "cmd가 cd인가?",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 766,
			"versionNonce": 735309838,
			"isDeleted": false,
			"id": "pjM6GJmMpyEdYQO-C-uHb",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1110.9702974955244,
			"y": 650.0539667451585,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 112.85783386230469,
			"height": 0.45465087890625,
			"seed": 1012184637,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "MDrJZHS7"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "AtGFDHk6sDbRnxbXe5tHJ",
				"gap": 2.3178558349609375,
				"focus": -0.07667268804142063
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-112.85783386230469,
					0.45465087890625
				]
			]
		},
		{
			"type": "text",
			"version": 92,
			"versionNonce": 531455954,
			"isDeleted": false,
			"id": "MDrJZHS7",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -793.4276313781738,
			"y": 649.8459080700281,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1237998483,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "pjM6GJmMpyEdYQO-C-uHb",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 468,
			"versionNonce": 70696526,
			"isDeleted": false,
			"id": "AtGFDHk6sDbRnxbXe5tHJ",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1379.5629717508955,
			"y": 588.1053278291429,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 153.41698455810547,
			"height": 135.911376953125,
			"seed": 633988925,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 358,
			"versionNonce": 240489874,
			"isDeleted": false,
			"id": "ZN1naXKl",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1354.634440104167,
			"y": 643.5610163057054,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 103.55992126464844,
			"height": 25,
			"seed": 1888722461,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "ft_cd 실행",
			"rawText": "ft_cd 실행",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "AtGFDHk6sDbRnxbXe5tHJ",
			"originalText": "ft_cd 실행",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 1187,
			"versionNonce": 1537590414,
			"isDeleted": false,
			"id": "euRjN5ag-K66kdfpKSvV4",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1004.1155237479966,
			"y": 755.5421835701212,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 1.701302449515424,
			"height": 84.33501787177522,
			"seed": 713218515,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "yNlahHJ6"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					1.701302449515424,
					84.33501787177522
				]
			]
		},
		{
			"type": "text",
			"version": 91,
			"versionNonce": 1844515666,
			"isDeleted": false,
			"id": "yNlahHJ6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -624.5094261169434,
			"y": 810.50310411495,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 305207709,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "euRjN5ag-K66kdfpKSvV4",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "diamond",
			"version": 508,
			"versionNonce": 1943667406,
			"isDeleted": false,
			"id": "-NzEpyPXQaCDKgdYZB2En",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1126.9841524759931,
			"y": 847.0757278914953,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 253.60690307617185,
			"height": 270,
			"seed": 1081996733,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 519,
			"versionNonce": 1356257554,
			"isDeleted": false,
			"id": "MJH5dMK2",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1051.9823900858564,
			"y": 944.5757278914953,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 103.7999267578125,
			"height": 75,
			"seed": 1937668413,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "자식\n프로세스에서\ncmd 실행",
			"rawText": "자식 프로세스에서 cmd 실행",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "-NzEpyPXQaCDKgdYZB2En",
			"originalText": "자식 프로세스에서 cmd 실행",
			"lineHeight": 1.25,
			"baseline": 68
		},
		{
			"type": "diamond",
			"version": 448,
			"versionNonce": 1869379854,
			"isDeleted": false,
			"id": "QU5pfgVPZvgNlKLv02Fuh",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -759.534881955101,
			"y": 546.9260396278426,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 191.31487165178578,
			"height": 175.8924211774555,
			"seed": 896966301,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 370,
			"versionNonce": 1719527122,
			"isDeleted": false,
			"id": "yGrokf01",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -702.7061335245764,
			"y": 609.8991449222065,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 77.99993896484375,
			"height": 50,
			"seed": 1236084957,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "마지막\ncmd인가?",
			"rawText": "마지막 cmd인가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "QU5pfgVPZvgNlKLv02Fuh",
			"originalText": "마지막 cmd인가?",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 1258,
			"versionNonce": 903227214,
			"isDeleted": false,
			"id": "qNyuN6fe3bbGG36SjGCw5",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -661.0867697089363,
			"y": 723.0892097233249,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 4.510048552528588,
			"height": 96.59025659257611,
			"seed": 384398557,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "T7v2dtmS"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					4.510048552528588,
					96.59025659257611
				]
			]
		},
		{
			"type": "text",
			"version": 104,
			"versionNonce": 1467825298,
			"isDeleted": false,
			"id": "T7v2dtmS",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -325.5337916782917,
			"y": 774.8315891767637,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 107.97990417480469,
			"height": 25,
			"seed": 539827731,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no(mid cmd)",
			"rawText": "no(mid cmd)",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "qNyuN6fe3bbGG36SjGCw5",
			"originalText": "no(mid cmd)",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 842,
			"versionNonce": 1466961294,
			"isDeleted": false,
			"id": "xG5ChkiI0VgzWRksyNk9I",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -563.7074577360513,
			"y": 632.1499085520184,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 116.09553197514697,
			"height": 1.1109277271890505,
			"seed": 672557373,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "tLIPMmca"
				}
			],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					116.09553197514697,
					-1.1109277271890505
				]
			]
		},
		{
			"type": "text",
			"version": 92,
			"versionNonce": 562813522,
			"isDeleted": false,
			"id": "tLIPMmca",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -116.61578478131895,
			"y": 631.6245404881477,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1679204435,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "xG5ChkiI0VgzWRksyNk9I",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "rectangle",
			"version": 398,
			"versionNonce": 1903373262,
			"isDeleted": false,
			"id": "k1kIAIBmMZrOU4rvo3Diw",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -434.197270347958,
			"y": 548.0343914500406,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 214.2681884765626,
			"height": 169.15113176618308,
			"seed": 2017457245,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 501,
			"versionNonce": 1937817618,
			"isDeleted": false,
			"id": "u61wo1qW",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -428.1031159900478,
			"y": 582.6099573331321,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 202.0798797607422,
			"height": 100,
			"seed": 1372140317,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로\nredirection, cmd를\n실행",
			"rawText": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로 redirection, cmd를 실행",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "k1kIAIBmMZrOU4rvo3Diw",
			"originalText": "1. 자식 프로세스를 연다.\n2. 표준 입력을 pipe로 redirection, cmd를 실행",
			"lineHeight": 1.25,
			"baseline": 93
		},
		{
			"type": "rectangle",
			"version": 534,
			"versionNonce": 301498894,
			"isDeleted": false,
			"id": "r8R_jPiyqoEbtxbybRZ4u",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -822.4985747564403,
			"y": 837.3691518434562,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 335.50885881696433,
			"height": 166.7016601562501,
			"seed": 1832187229,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 761,
			"versionNonce": 156429778,
			"isDeleted": false,
			"id": "gbvsKCeG",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -792.2240342639739,
			"y": 870.7199819215812,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 274.95977783203125,
			"height": 100,
			"seed": 1984961149,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을\nredirection, 두번째 pipe로 표준\n출력을 redirection, cmd를 실행",
			"rawText": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을 redirection, 두번째 pipe로 표준 출력을 redirection, cmd를 실행",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "r8R_jPiyqoEbtxbybRZ4u",
			"originalText": "1. 두번째 pipe를 열고 fork\n2. 첫번째 pipe로 표준 입력을 redirection, 두번째 pipe로 표준 출력을 redirection, cmd를 실행",
			"lineHeight": 1.25,
			"baseline": 93
		},
		{
			"type": "diamond",
			"version": 608,
			"versionNonce": 469307470,
			"isDeleted": false,
			"id": "1tVAwC5j9kiE558cU_ghJ",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1125.1743990580244,
			"y": 243.16600415685014,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 231.27841186523435,
			"height": 189.96331787109375,
			"seed": 1100740371,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 635,
			"versionNonce": 135881618,
			"isDeleted": false,
			"id": "3ghEIm5q",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1057.2647616068525,
			"y": 300.6568336246236,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 95.81993103027344,
			"height": 75,
			"seed": 910200819,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "cmd 뒤에\nPIPE가\n존재하는가?",
			"rawText": "cmd 뒤에  PIPE가 \n존재하는가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "1tVAwC5j9kiE558cU_ghJ",
			"originalText": "cmd 뒤에  PIPE가 \n존재하는가?",
			"lineHeight": 1.25,
			"baseline": 68
		},
		{
			"type": "rectangle",
			"version": 464,
			"versionNonce": 726521486,
			"isDeleted": false,
			"id": "F-cf99_OFLVwhbVBTtAjk",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1556.669394175212,
			"y": 251.9735929399053,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 319.6088562011719,
			"height": 167.33294677734372,
			"seed": 1750770077,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 716,
			"versionNonce": 1510678866,
			"isDeleted": false,
			"id": "xhAb0NSv",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1543.974859873454,
			"y": 285.6400663285772,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 294.21978759765625,
			"height": 100,
			"seed": 697722429,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280906,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의\nWRITE로 redirection, execve로\ncmd를 실행한다.",
			"rawText": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의 WRITE로 redirection, execve로 cmd를 실행한다. ",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "F-cf99_OFLVwhbVBTtAjk",
			"originalText": "1. pipe 하나를 열고 fork\n2. 자식에서 표준 출력을 pipe의 WRITE로 redirection, execve로 cmd를 실행한다. ",
			"lineHeight": 1.25,
			"baseline": 93
		},
		{
			"type": "rectangle",
			"version": 273,
			"versionNonce": 2024789198,
			"isDeleted": false,
			"id": "nE6mSUKFTnqDgAAPee_iA",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "dotted",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1580.5640624515581,
			"y": 184.6321403401979,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 1378.1947157118066,
			"height": 914.7397189670146,
			"seed": 1362570579,
			"groupIds": [
				"AmiG_k-swf3tZ-23kItMz"
			],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 158,
			"versionNonce": 176105234,
			"isDeleted": false,
			"id": "EU1enNzAFnkDWZEu8g_CW",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -117.51422046479433,
			"y": 506.949950398792,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 251.86503092447947,
			"height": 127.94989691840283,
			"seed": 1548453277,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
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
			"updated": 1728023280906,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 158,
			"versionNonce": 1035471630,
			"isDeleted": false,
			"id": "ImpBiiGL",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -80.88162413097257,
			"y": 558.4248988579934,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 178.59983825683594,
			"height": 25,
			"seed": 1787804509,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "go_to_next_node",
			"rawText": "go_to_next_node",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "EU1enNzAFnkDWZEu8g_CW",
			"originalText": "go_to_next_node",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 86,
			"versionNonce": 569144530,
			"isDeleted": false,
			"id": "W-gbpyKASOZ5I7x8dF7Ac",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 263.39689878433785,
			"y": 387.6309671088612,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 120.34261067708348,
			"height": 187.29566786024327,
			"seed": 954370067,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
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
			]
		},
		{
			"type": "arrow",
			"version": 150,
			"versionNonce": 417298766,
			"isDeleted": false,
			"id": "PfjOWXmkROGl-mRaXlo_X",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -198.71111987885695,
			"y": 561.4752325168475,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 83.23744032118066,
			"height": 1.5848795572916288,
			"seed": 953839965,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "nE6mSUKFTnqDgAAPee_iA",
				"focus": -0.19919028555638266,
				"gap": 3.658226860894615
			},
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					83.23744032118066,
					1.5848795572916288
				]
			]
		},
		{
			"type": "arrow",
			"version": 243,
			"versionNonce": 32115346,
			"isDeleted": false,
			"id": "hI0YGZHEp9mp499lYt_-U",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 3.7660936628089985,
			"y": 633.8369610408134,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 2.641426444317415,
			"height": 69.07004451137789,
			"seed": 1295325405,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "LDW3KJHpj9ZHQb80AnUp3",
				"gap": 5.733155307528932,
				"focus": 0.010209091487069551
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					2.641426444317415,
					69.07004451137789
				]
			]
		},
		{
			"type": "diamond",
			"version": 263,
			"versionNonce": 1904156558,
			"isDeleted": false,
			"id": "LDW3KJHpj9ZHQb80AnUp3",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -171.9866732642745,
			"y": 708.4632902508831,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 359.61452907986154,
			"height": 158.78851996527786,
			"seed": 857934835,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280907,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 143,
			"versionNonce": 1093593170,
			"isDeleted": false,
			"id": "mvIk1Ww6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -73.99296836247316,
			"y": 762.6604202422026,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 163.81985473632812,
			"height": 50,
			"seed": 256595933,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "parse_list의 끝에\n도달하였는가?",
			"rawText": "parse_list의 끝에 도달하였는가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "LDW3KJHpj9ZHQb80AnUp3",
			"originalText": "parse_list의 끝에 도달하였는가?",
			"lineHeight": 1.25,
			"baseline": 43
		},
		{
			"type": "arrow",
			"version": 87,
			"versionNonce": 1540357582,
			"isDeleted": false,
			"id": "N2VeoGExp6ra7tzslX25q",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 185.55921762346634,
			"y": 785.8509928691811,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 341.83730993534357,
			"height": 822.556506801307,
			"seed": 1442474579,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "x9B0h64y"
				}
			],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
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
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
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
			]
		},
		{
			"type": "text",
			"version": 9,
			"versionNonce": 127012370,
			"isDeleted": false,
			"id": "x9B0h64y",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 494.3144301157172,
			"y": 321.4776131675494,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 1323219059,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "N2VeoGExp6ra7tzslX25q",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "arrow",
			"version": 204,
			"versionNonce": 2095780878,
			"isDeleted": false,
			"id": "q2WUslEi7sCGPsa92msa9",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 5.562290494405943,
			"y": 865.970411019112,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.5463876183309191,
			"height": 106.06793720269297,
			"seed": 1583502515,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "8Knk1zfn"
				}
			],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": {
				"elementId": "0dtl-WH2-sD19VTITHJs8",
				"gap": 21.220397949218807,
				"focus": 0.0441515337609202
			},
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					-0.5463876183309191,
					106.06793720269297
				]
			]
		},
		{
			"type": "text",
			"version": 10,
			"versionNonce": 1779071954,
			"isDeleted": false,
			"id": "8Knk1zfn",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -8.723504929313663,
			"y": 903.3831646540948,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1619307229,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "q2WUslEi7sCGPsa92msa9",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 18
		},
		{
			"type": "ellipse",
			"version": 209,
			"versionNonce": 1858691662,
			"isDeleted": false,
			"id": "0dtl-WH2-sD19VTITHJs8",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -99.01093812972613,
			"y": 993.2004321779666,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 198.5216606987849,
			"height": 106.56100802951417,
			"seed": 903270141,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
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
			"updated": 1728023280907,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 8,
			"versionNonce": 1185886610,
			"isDeleted": false,
			"id": "NUXNTJc4",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -15.768100598862162,
			"y": 1033.805930498852,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.65997314453125,
			"height": 25,
			"seed": 829555901,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1728023280907,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "end",
			"rawText": "end",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "0dtl-WH2-sD19VTITHJs8",
			"originalText": "end",
			"lineHeight": 1.25,
			"baseline": 18
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
		"scrollX": 1916.6648247128423,
		"scrollY": 1167.5316016914594,
		"zoom": {
			"value": 0.8
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