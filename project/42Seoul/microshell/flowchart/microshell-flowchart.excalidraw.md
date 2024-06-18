---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
start
parse_line으로부터 parse_list를 넘겨받는다. ^TdAlpDw3

pipe_fd, pipe_fd_2, first_cmd를 초기화 ^CpOgMOAQ

parse_list의 끝에 도달하였는가? ^aQAwrp0Y

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
			"version": 245,
			"versionNonce": 866087165,
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
			"updated": 1718676612556,
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
			"version": 299,
			"versionNonce": 1829366099,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
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
			"x": -4.357264489678543,
			"y": -253.58597428801613,
			"width": 1.1851997582801985,
			"height": 31.56416736531247,
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
			"version": 162,
			"versionNonce": 803359069,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-1.1851997582801985,
					31.56416736531247
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
			"version": 171,
			"versionNonce": 1833387763,
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
			"updated": 1718676612556,
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
			"version": 140,
			"versionNonce": 1659573693,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
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
			"x": -5.3194340861076705,
			"y": -145.59407254770366,
			"width": 1.8055324567882804,
			"height": 39.22832984365071,
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
			"version": 751,
			"versionNonce": 1699213459,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					1.8055324567882804,
					39.22832984365071
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
			"version": 507,
			"versionNonce": 381838899,
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
				}
			],
			"updated": 1718676612556,
			"link": null,
			"locked": false
		},
		{
			"id": "aQAwrp0Y",
			"type": "text",
			"x": -92.35633850097656,
			"y": -64.25081082895366,
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
			"seed": 1302912157,
			"version": 565,
			"versionNonce": 2040826493,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
			"link": null,
			"locked": false,
			"text": "parse_list의 끝에\n도달하였는가?",
			"rawText": "parse_list의 끝에 도달하였는가?",
			"fontSize": 20,
			"fontFamily": 1,
			"textAlign": "center",
			"verticalAlign": "middle",
			"baseline": 42,
			"containerId": "eMRLaDVmsHbOypzWeesJz",
			"originalText": "parse_list의 끝에 도달하였는가?",
			"lineHeight": 1.25
		},
		{
			"id": "8Mxo_eQ0Nam1UPacnFzWk",
			"type": "arrow",
			"x": -7.071960899121494,
			"y": 26.086915473319962,
			"width": 0.007542730097236827,
			"height": 55.3337993412629,
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
			"version": 141,
			"versionNonce": 1218258899,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "1mwFaf2j"
				}
			],
			"updated": 1718676612556,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					0.007542730097236827,
					55.3337993412629
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
			"version": 8,
			"versionNonce": 2030580445,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
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
			"version": 167,
			"versionNonce": 1223387261,
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
			"updated": 1718676642846,
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
			"version": 90,
			"versionNonce": 848809789,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676612556,
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
			"x": -156.53715133666992,
			"y": 157.46448717651907,
			"width": 115.14650656888807,
			"height": 102.93581938394743,
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
			"version": 105,
			"versionNonce": 440179645,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "YfcFH3Vm"
				}
			],
			"updated": 1718676738201,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-106.02317810058594,
					8.37982177734375
				],
				[
					-115.14650656888807,
					102.93581938394743
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"focus": 0.12839397758835272,
				"gap": 3.190586762384541
			},
			"endBinding": {
				"elementId": "5pQRl2SNRgr3eUBGu9Jsu",
				"gap": 8.161162706991377,
				"focus": -0.07626038370691651
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
			"version": 16,
			"versionNonce": 628681821,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676653666,
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
			"x": -3.512432098388672,
			"y": 217.44294176636282,
			"width": 0.017852783203125,
			"height": 79.23431396484375,
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
			"version": 36,
			"versionNonce": 124980157,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "kDdUqVXE"
				}
			],
			"updated": 1718676658879,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					0.017852783203125,
					79.23431396484375
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"focus": -0.0216471128009358,
				"gap": 3.271592090890721
			},
			"endBinding": null,
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
			"version": 5,
			"versionNonce": 330366813,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676657620,
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
			"id": "fiM2lTLJTs5SjZrAZ9Omg",
			"type": "arrow",
			"x": 140.45491409301758,
			"y": 151.81843004761282,
			"width": 114.578369140625,
			"height": 103.6578369140625,
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
			"version": 141,
			"versionNonce": 532856083,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "SRPVMbzL"
				}
			],
			"updated": 1718676705175,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					107.82696533203125,
					5.76190185546875
				],
				[
					114.578369140625,
					103.6578369140625
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"focus": -0.1556077246926263,
				"gap": 1
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
			"version": 6,
			"versionNonce": 868243347,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676676814,
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
			"version": 70,
			"versionNonce": 1298104691,
			"isDeleted": false,
			"boundElements": [
				{
					"id": "fiM2lTLJTs5SjZrAZ9Omg",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "CGSCc1Tz"
				}
			],
			"updated": 1718676688803,
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
			"version": 76,
			"versionNonce": 825611731,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676703936,
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
			"id": "5pQRl2SNRgr3eUBGu9Jsu",
			"type": "diamond",
			"x": -363.21088790893555,
			"y": 268.32937492507915,
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
			"version": 138,
			"versionNonce": 76902067,
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
			"updated": 1718676752145,
			"link": null,
			"locked": false
		},
		{
			"id": "ixOzTW7m",
			"type": "text",
			"x": -312.41347885131836,
			"y": 326.28596367019634,
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
			"version": 32,
			"versionNonce": 919225171,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676738139,
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
			"x": -361.6805534362793,
			"y": 350.6957689680479,
			"width": 133.06379321825375,
			"height": 3.4181027278425518,
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
			"version": 404,
			"versionNonce": 1648492733,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "ImKQfSgh"
				}
			],
			"updated": 1718676810753,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-133.06379321825375,
					-3.4181027278425518
				]
			],
			"lastCommittedPoint": null,
			"startBinding": null,
			"endBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 10.02903372623139,
				"focus": -0.06476476588950933
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
			"version": 14,
			"versionNonce": 1198897117,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676759998,
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
			"x": -276.1642875671387,
			"y": 434.75002922195415,
			"width": 2.433746337890625,
			"height": 112.38531494140625,
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
			"version": 48,
			"versionNonce": 462047965,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "NtthsPTB"
				}
			],
			"updated": 1718676763650,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					2.433746337890625,
					112.38531494140625
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "5pQRl2SNRgr3eUBGu9Jsu",
				"focus": 0.04862497263445731,
				"gap": 2.1669156246953136
			},
			"endBinding": null,
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
			"version": 3,
			"versionNonce": 143237757,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676762665,
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
			"id": "1tVAwC5j9kiE558cU_ghJ",
			"type": "diamond",
			"x": -735.6128349304199,
			"y": 255.23062004226665,
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
			"version": 280,
			"versionNonce": 1732143133,
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
			"updated": 1718676927113,
			"link": null,
			"locked": false
		},
		{
			"id": "3ghEIm5q",
			"type": "text",
			"x": -667.703197479248,
			"y": 312.7214495100401,
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
			"version": 310,
			"versionNonce": 1920635997,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676810752,
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
			"id": "Ey1jaK3BNLMCEc0sgH_A6",
			"type": "arrow",
			"x": -735.7569061173374,
			"y": 349.0365364380555,
			"width": 96.73562852011378,
			"height": 1.2645815870292267,
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
			"version": 299,
			"versionNonce": 1323370067,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "XYYrdpbF"
				}
			],
			"updated": 1718676920064,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-96.73562852011378,
					-1.2645815870292267
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 1,
				"focus": -0.003566119803225936
			},
			"endBinding": {
				"elementId": "F-cf99_OFLVwhbVBTtAjk",
				"gap": 15.006439208984375,
				"focus": -0.025863658432051437
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
			"version": 10,
			"versionNonce": 877643219,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676823726,
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
			"id": "F-cf99_OFLVwhbVBTtAjk",
			"type": "rectangle",
			"x": -1167.1078300476074,
			"y": 264.0382088253218,
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
			"version": 185,
			"versionNonce": 445153203,
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
			"updated": 1718676868729,
			"link": null,
			"locked": false
		},
		{
			"id": "xhAb0NSv",
			"type": "text",
			"x": -1154.4132957458496,
			"y": 297.7046822139937,
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
			"version": 440,
			"versionNonce": 1267593021,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676917796,
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
			"id": "cND-KRhE_XOx2i9nk6aZa",
			"type": "arrow",
			"x": -618.9959831237793,
			"y": 445.69206895869996,
			"width": 2.2869350122045944,
			"height": 110.23655111706017,
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
			"version": 47,
			"versionNonce": 974518749,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "Mw7TQbMl"
				}
			],
			"updated": 1718676949752,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					2.2869350122045944,
					110.23655111706017
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "1tVAwC5j9kiE558cU_ghJ",
				"gap": 1.005451874344402,
				"focus": 0.008674823656159512
			},
			"endBinding": {
				"elementId": "6hHfwv__MFMv-8IHEmJPG",
				"gap": 2.9618076555007065,
				"focus": 0.03077927044010847
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
			"version": 11,
			"versionNonce": 2006692179,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676933642,
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
			"x": -723.646312713623,
			"y": 558.7044590954188,
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
			"version": 140,
			"versionNonce": 678096093,
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
			"updated": 1718676977562,
			"link": null,
			"locked": false
		},
		{
			"id": "KxjWML7L",
			"type": "text",
			"x": -650.3641395568848,
			"y": 638.4828099254969,
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
			"version": 26,
			"versionNonce": 654145939,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676949690,
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
			"x": -721.4087333679199,
			"y": 662.118582630575,
			"width": 112.8578338623048,
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
			"version": 81,
			"versionNonce": 536238131,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "MDrJZHS7"
				}
			],
			"updated": 1718676972329,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-112.8578338623048,
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
			"version": 8,
			"versionNonce": 1107075709,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676957917,
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
			"x": -990.001407623291,
			"y": 600.1699437145594,
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
			"version": 124,
			"versionNonce": 1251122739,
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
			"updated": 1718676969122,
			"link": null,
			"locked": false
		},
		{
			"id": "ZN1naXKl",
			"type": "text",
			"x": -965.0728759765625,
			"y": 655.6256321911219,
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
			"version": 14,
			"versionNonce": 1416607987,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676971288,
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
			"x": -615.2161674499512,
			"y": 768.2605809215906,
			"width": 1.833465576171875,
			"height": 109.48504638671875,
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
			"version": 35,
			"versionNonce": 1356663123,
			"isDeleted": false,
			"boundElements": [
				{
					"type": "text",
					"id": "yNlahHJ6"
				}
			],
			"updated": 1718676985555,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					1.833465576171875,
					109.48504638671875
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "6hHfwv__MFMv-8IHEmJPG",
				"focus": -0.0072471119637288915,
				"gap": 2.0896192628174504
			},
			"endBinding": null,
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
			"version": 7,
			"versionNonce": 901806003,
			"isDeleted": false,
			"boundElements": null,
			"updated": 1718676984537,
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
			"id": "nw9DQrXBWn3WyypkcJdTb",
			"type": "rectangle",
			"x": -115.8769645690918,
			"y": -48.04738065317241,
			"width": 146.92703247070312,
			"height": 135.1922607421875,
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
			"seed": 440816979,
			"version": 31,
			"versionNonce": 1742427677,
			"isDeleted": true,
			"boundElements": null,
			"updated": 1718676612556,
			"link": null,
			"locked": false
		},
		{
			"id": "VvJh9dx622ryVE_mNVmak",
			"type": "arrow",
			"x": -105.05741500854492,
			"y": 189.31092272339407,
			"width": 91.31085205078125,
			"height": 57.158447265625,
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
			"seed": 933453843,
			"version": 124,
			"versionNonce": 1056804627,
			"isDeleted": true,
			"boundElements": null,
			"updated": 1718676612556,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					-91.31085205078125,
					57.158447265625
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"focus": 0.4173664598585456,
				"gap": 13.183096514228865
			},
			"endBinding": null,
			"startArrowhead": null,
			"endArrowhead": "arrow"
		},
		{
			"id": "IANbrzxjDrg-1iWaNFzB9",
			"type": "arrow",
			"x": 142.49641799926758,
			"y": 155.62800036011282,
			"width": 122.545166015625,
			"height": 105.91326904296875,
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
			"seed": 431319827,
			"version": 131,
			"versionNonce": 2003933587,
			"isDeleted": true,
			"boundElements": null,
			"updated": 1718676636286,
			"link": null,
			"locked": false,
			"points": [
				[
					0,
					0
				],
				[
					98.12469482421875,
					8.4927978515625
				],
				[
					122.545166015625,
					105.91326904296875
				]
			],
			"lastCommittedPoint": null,
			"startBinding": {
				"elementId": "N0bwk0I_LBNWpL3Pkpm_P",
				"focus": -0.17575665484318903,
				"gap": 1.3186561448243168
			},
			"endBinding": null,
			"startArrowhead": null,
			"endArrowhead": "arrow"
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
		"scrollX": 1066.457275390625,
		"scrollY": -191.99594774287968,
		"zoom": {
			"value": 1
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