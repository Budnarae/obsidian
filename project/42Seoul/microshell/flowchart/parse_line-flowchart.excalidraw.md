---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Text Elements
start(커맨드(argv)를 입력으로 받음) ^Bds4ZIqz

parse_list의 head malloc ^lC1z5Nw8

loop ^LZcgGs5w

find_cmd_len
cmd의 길이를 구한다 ^dg3kiBP9

cmd_len을 전달 ^auFt32vC

cmd_len > 0 ^JtB9VHBK

yes(type : cmd) ^jT8JEsbX

no ^flpszI8m

malloc_cmd ^c2JAPM0g

no(type : PIPE or SEMICOLON) ^73qgS8ks

check_syntax_type으로 type이 PIPE인지 SEMICOLON인지 확인 ^ZD5WWhci

parse_list를 완성하였는가? ^Cb9YXq6s

list의 다음 node를 malloc ^YbEY5aHP

no ^VDE0fR61

yes ^Cr05Mcr6

end
microshell에게 parse_list를 넘긴다 ^LJ7mqdQj

[[microshell-flowchart.excalidraw]] ^y5JHn7C6

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
			"version": 112,
			"versionNonce": 722291069,
			"isDeleted": false,
			"id": "Tcm4uImg9cG1AewBg7jgs",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -152.49575805664062,
			"y": -423.69154357910156,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 302.6529541015625,
			"height": 85,
			"seed": 963057220,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "Bds4ZIqz"
				},
				{
					"id": "QY11Cen1TPvVTZ82D2czj",
					"type": "arrow"
				}
			],
			"updated": 1718676036810,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 105,
			"versionNonce": 1315166419,
			"isDeleted": false,
			"id": "Bds4ZIqz",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -96.36317761960368,
			"y": -406.24358177952985,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 190.3798370361328,
			"height": 50,
			"seed": 1616692220,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "start(커맨드(argv)를\n입력으로 받음)",
			"rawText": "start(커맨드(argv)를 입력으로 받음)",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "Tcm4uImg9cG1AewBg7jgs",
			"originalText": "start(커맨드(argv)를 입력으로 받음)",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 163,
			"versionNonce": 736822290,
			"isDeleted": false,
			"id": "QY11Cen1TPvVTZ82D2czj",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -2.4649859504525105,
			"y": -331.3324824805702,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 1.1492127320900107,
			"height": 23.52976336435927,
			"seed": 334095556,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1718685335270,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "Tcm4uImg9cG1AewBg7jgs",
				"gap": 7.360723225717692,
				"focus": -0.007533474081874304
			},
			"endBinding": {
				"elementId": "YSDmwM9NXEaKcZsX7SrEP",
				"gap": 4.97442626953125,
				"focus": -0.022057998459953827
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
					-1.1492127320900107,
					23.52976336435927
				]
			]
		},
		{
			"type": "rectangle",
			"version": 91,
			"versionNonce": 2092385907,
			"isDeleted": false,
			"id": "YSDmwM9NXEaKcZsX7SrEP",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -106.80465698242188,
			"y": -302.8282928466797,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 206.92333984375,
			"height": 74.03106689453125,
			"seed": 523879620,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "QY11Cen1TPvVTZ82D2czj",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "lC1z5Nw8"
				},
				{
					"id": "J6yCGVJOd31B_9PtayQQp",
					"type": "arrow"
				}
			],
			"updated": 1718676036810,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 52,
			"versionNonce": 1109184061,
			"isDeleted": false,
			"id": "lC1z5Nw8",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -90.72290802001953,
			"y": -290.81275939941406,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 174.7598419189453,
			"height": 50,
			"seed": 1430607868,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "parse_list의 head\nmalloc",
			"rawText": "parse_list의 head malloc",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "YSDmwM9NXEaKcZsX7SrEP",
			"originalText": "parse_list의 head malloc",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 180,
			"versionNonce": 1690783886,
			"isDeleted": false,
			"id": "J6yCGVJOd31B_9PtayQQp",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -2.3875639739297316,
			"y": -225.8196563720703,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.30596041185806344,
			"height": 55.020504350528086,
			"seed": 28932292,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1718685443709,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "YSDmwM9NXEaKcZsX7SrEP",
				"gap": 2.977569580078125,
				"focus": -0.006839135173767999
			},
			"endBinding": {
				"elementId": "yOIKhkwYdk4pM4M2t9bgi",
				"gap": 3.869784535167078,
				"focus": 0.00904443094914261
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
					0.30596041185806344,
					55.020504350528086
				]
			]
		},
		{
			"type": "diamond",
			"version": 159,
			"versionNonce": 2029413262,
			"isDeleted": false,
			"id": "yOIKhkwYdk4pM4M2t9bgi",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -109.04825661399153,
			"y": -166.9435771595348,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 213.27066040039065,
			"height": 220,
			"seed": 536144708,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"id": "J6yCGVJOd31B_9PtayQQp",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "LZcgGs5w"
				},
				{
					"id": "AcXnP8AokeOfLBFFmb60L",
					"type": "arrow"
				},
				{
					"id": "IbQrATLSrZrsY1jmduXYn",
					"type": "arrow"
				}
			],
			"updated": 1718685421020,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 221,
			"versionNonce": 495068690,
			"isDeleted": false,
			"id": "LZcgGs5w",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -20.870568015358707,
			"y": -69.44357715953481,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 37.27995300292969,
			"height": 25,
			"seed": 359565636,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718685424895,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "loop",
			"rawText": "loop",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "yOIKhkwYdk4pM4M2t9bgi",
			"originalText": "loop",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "arrow",
			"version": 83,
			"versionNonce": 1855653134,
			"isDeleted": false,
			"id": "AcXnP8AokeOfLBFFmb60L",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -0.7618592224796623,
			"y": 56.220228938928315,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.21564267670612036,
			"height": 95.26413372377958,
			"seed": 772427844,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "flpszI8m"
				}
			],
			"updated": 1718685443709,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "yOIKhkwYdk4pM4M2t9bgi",
				"gap": 3.5687101169630324,
				"focus": -0.012912502388431522
			},
			"endBinding": {
				"elementId": "ZtqrakdxYdkWCfv5iTG9n",
				"gap": 3.2214683874429397,
				"focus": -0.0024866422147481497
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
					0.21564267670612036,
					95.26413372377958
				]
			]
		},
		{
			"type": "text",
			"version": 6,
			"versionNonce": 1807963987,
			"isDeleted": false,
			"id": "flpszI8m",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -10.722824260260346,
			"y": 91.56907192548289,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 1256175556,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "AcXnP8AokeOfLBFFmb60L",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "rectangle",
			"version": 108,
			"versionNonce": 641645405,
			"isDeleted": false,
			"id": "ZtqrakdxYdkWCfv5iTG9n",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -137.01376342773438,
			"y": 154.70583105015083,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 273.920654296875,
			"height": 127.72167968749997,
			"seed": 1345771388,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "AcXnP8AokeOfLBFFmb60L",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "dg3kiBP9"
				},
				{
					"id": "ssUnqPZSNhlfv3M3-IvAR",
					"type": "arrow"
				}
			],
			"updated": 1718676036810,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 76,
			"versionNonce": 1856173299,
			"isDeleted": false,
			"id": "dg3kiBP9",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -87.64337921142578,
			"y": 193.56667089390083,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 175.1798858642578,
			"height": 50,
			"seed": 821046652,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "find_cmd_len\ncmd의 길이를 구한다",
			"rawText": "find_cmd_len\ncmd의 길이를 구한다",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "ZtqrakdxYdkWCfv5iTG9n",
			"originalText": "find_cmd_len\ncmd의 길이를 구한다",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 502,
			"versionNonce": 99141330,
			"isDeleted": false,
			"id": "ssUnqPZSNhlfv3M3-IvAR",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1.9390907374190098,
			"y": 286.0261130325727,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 0.42405972439382134,
			"height": 142.20202178816697,
			"seed": 967642692,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "auFt32vC"
				}
			],
			"updated": 1718685335272,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "ZtqrakdxYdkWCfv5iTG9n",
				"gap": 3.598602294921932,
				"focus": 0.012281988222103723
			},
			"endBinding": {
				"elementId": "gJtZKV0XR74PrTarZhUHQ",
				"gap": 9.255768752249892,
				"focus": -0.029212760877154884
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
					-0.42405972439382134,
					142.20202178816697
				]
			]
		},
		{
			"type": "text",
			"version": 30,
			"versionNonce": 1526587027,
			"isDeleted": false,
			"id": "auFt32vC",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -70.6661605834961,
			"y": 340.2144064896039,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 138.03990173339844,
			"height": 25,
			"seed": 794561404,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "cmd_len을 전달",
			"rawText": "cmd_len을 전달",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "ssUnqPZSNhlfv3M3-IvAR",
			"originalText": "cmd_len을 전달",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "diamond",
			"version": 318,
			"versionNonce": 1128482845,
			"isDeleted": false,
			"id": "gJtZKV0XR74PrTarZhUHQ",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -133.2161865234375,
			"y": 436.70555472878846,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 269.1364440917969,
			"height": 127.8583984375,
			"seed": 491186556,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"id": "ssUnqPZSNhlfv3M3-IvAR",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "JtB9VHBK"
				},
				{
					"id": "KQf_VwQIYN9NGExjWJ-MP",
					"type": "arrow"
				},
				{
					"id": "T9I3YpWgcqzqXHHlqFt-9",
					"type": "arrow"
				}
			],
			"updated": 1718676036810,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 291,
			"versionNonce": 2072679475,
			"isDeleted": false,
			"id": "JtB9VHBK",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -58.23204040527344,
			"y": 488.17015433816346,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 119.59992980957031,
			"height": 25,
			"seed": 1924533060,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "cmd_len > 0",
			"rawText": "cmd_len > 0",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "gJtZKV0XR74PrTarZhUHQ",
			"originalText": "cmd_len > 0",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "arrow",
			"version": 224,
			"versionNonce": 1674445138,
			"isDeleted": false,
			"id": "KQf_VwQIYN9NGExjWJ-MP",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -88.72570609955977,
			"y": 538.1894741131218,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 109.24334681513903,
			"height": 94.86401491471179,
			"seed": 1476765508,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "jT8JEsbX"
				}
			],
			"updated": 1718685335274,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "gJtZKV0XR74PrTarZhUHQ",
				"gap": 14.830217658159597,
				"focus": 0.34800592493532984
			},
			"endBinding": {
				"elementId": "9pLvSd4ZCfq9x5AetMrPw",
				"gap": 9.375875510974481,
				"focus": -0.5376344411042685
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
					-109.24334681513903,
					94.86401491471179
				]
			]
		},
		{
			"type": "text",
			"version": 29,
			"versionNonce": 3118547,
			"isDeleted": false,
			"id": "jT8JEsbX",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -175.1085662841797,
			"y": 569.7954595139447,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 146.63986206054688,
			"height": 25,
			"seed": 544905724,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes(type : cmd)",
			"rawText": "yes(type : cmd)",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "KQf_VwQIYN9NGExjWJ-MP",
			"originalText": "yes(type : cmd)",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "rectangle",
			"version": 115,
			"versionNonce": 256611219,
			"isDeleted": false,
			"id": "9pLvSd4ZCfq9x5AetMrPw",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -284.3817918565538,
			"y": 642.4293645388082,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 168.7034776475694,
			"height": 137.53153483072913,
			"seed": 81906172,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "KQf_VwQIYN9NGExjWJ-MP",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "c2JAPM0g"
				},
				{
					"id": "l9n8ua8kv3feWUQvl_PAi",
					"type": "arrow"
				}
			],
			"updated": 1718676052877,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 42,
			"versionNonce": 1476617075,
			"isDeleted": false,
			"id": "c2JAPM0g",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -254.15001000298392,
			"y": 698.6951319541727,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 108.23991394042969,
			"height": 25,
			"seed": 1398119236,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "malloc_cmd",
			"rawText": "malloc_cmd",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "9pLvSd4ZCfq9x5AetMrPw",
			"originalText": "malloc_cmd",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "arrow",
			"version": 343,
			"versionNonce": 1652672594,
			"isDeleted": false,
			"id": "T9I3YpWgcqzqXHHlqFt-9",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 108.4754775597421,
			"y": 529.6992604040091,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 107.61530521588782,
			"height": 98.73359403334302,
			"seed": 55121988,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "73qgS8ks"
				}
			],
			"updated": 1718685335280,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "gJtZKV0XR74PrTarZhUHQ",
				"gap": 14.475845385452828,
				"focus": -0.5606405307252722
			},
			"endBinding": {
				"elementId": "ySpAqdh986VDYHyvKwuWf",
				"gap": 11.704779730902601,
				"focus": 0.47173412058211295
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
					107.61530521588782,
					98.73359403334302
				]
			]
		},
		{
			"type": "text",
			"version": 47,
			"versionNonce": 1263303955,
			"isDeleted": false,
			"id": "73qgS8ks",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 39.501942952473826,
			"y": 559.8413763015014,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 175.53985595703125,
			"height": 50,
			"seed": 1794666108,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no(type : PIPE or\nSEMICOLON)",
			"rawText": "no(type : PIPE or SEMICOLON)",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "T9I3YpWgcqzqXHHlqFt-9",
			"originalText": "no(type : PIPE or SEMICOLON)",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "rectangle",
			"version": 319,
			"versionNonce": 591720061,
			"isDeleted": false,
			"id": "ySpAqdh986VDYHyvKwuWf",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 83.93631659613715,
			"y": 640.1376341682547,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 250.75554741753479,
			"height": 137.58768717447924,
			"seed": 1600071364,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"id": "T9I3YpWgcqzqXHHlqFt-9",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "ZD5WWhci"
				},
				{
					"id": "9g9FFlXp7M0rB6ls_PE7X",
					"type": "arrow"
				}
			],
			"updated": 1718676040813,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 286,
			"versionNonce": 1434542771,
			"isDeleted": false,
			"id": "ZD5WWhci",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 96.70418887668188,
			"y": 671.4314777554944,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 225.2198028564453,
			"height": 75,
			"seed": 814677500,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676036810,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "check_syntax_type으로\ntype이 PIPE인지\nSEMICOLON인지 확인",
			"rawText": "check_syntax_type으로 type이 PIPE인지 SEMICOLON인지 확인",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "ySpAqdh986VDYHyvKwuWf",
			"originalText": "check_syntax_type으로 type이 PIPE인지 SEMICOLON인지 확인",
			"lineHeight": 1.25,
			"baseline": 67
		},
		{
			"type": "diamond",
			"version": 324,
			"versionNonce": 847846675,
			"isDeleted": false,
			"id": "EYU2LhvULtLtUsVpHtrMM",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -128.62820423973926,
			"y": 866.6400309131445,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 268.1410217285156,
			"height": 152.28866577148438,
			"seed": 110723219,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "Cb9YXq6s"
				},
				{
					"id": "9g9FFlXp7M0rB6ls_PE7X",
					"type": "arrow"
				},
				{
					"id": "l9n8ua8kv3feWUQvl_PAi",
					"type": "arrow"
				},
				{
					"id": "sOLlucTFCZ4B9cVkeGCYD",
					"type": "arrow"
				},
				{
					"id": "CXp21EzAiSoIcYuGooOGn",
					"type": "arrow"
				}
			],
			"updated": 1718676216673,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 266,
			"versionNonce": 498349043,
			"isDeleted": false,
			"id": "Cb9YXq6s",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -54.20288838280567,
			"y": 917.7121973560156,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 119.21987915039062,
			"height": 50,
			"seed": 1938414899,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676071098,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "parse_list를\n완성하였는가?",
			"rawText": "parse_list를 완성하였는가?",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "EYU2LhvULtLtUsVpHtrMM",
			"originalText": "parse_list를 완성하였는가?",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 389,
			"versionNonce": 295309138,
			"isDeleted": false,
			"id": "9g9FFlXp7M0rB6ls_PE7X",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 207.44594105428098,
			"y": 780.66317274136,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 145.20527845415342,
			"height": 107.75661271252477,
			"seed": 840424339,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1718685335292,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "ySpAqdh986VDYHyvKwuWf",
				"gap": 2.9378513986259804,
				"focus": -0.43466922546035563
			},
			"endBinding": {
				"elementId": "EYU2LhvULtLtUsVpHtrMM",
				"gap": 9.111487013013786,
				"focus": -0.12276785762987577
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
					-145.20527845415342,
					107.75661271252477
				]
			]
		},
		{
			"type": "arrow",
			"version": 347,
			"versionNonce": 957866706,
			"isDeleted": false,
			"id": "l9n8ua8kv3feWUQvl_PAi",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -193.11005352381568,
			"y": 782.8547163204615,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 138.27336347498607,
			"height": 108.55682493251027,
			"seed": 402157853,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1718685335293,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "9pLvSd4ZCfq9x5AetMrPw",
				"gap": 2.893816950924304,
				"focus": 0.49060739996651204
			},
			"endBinding": {
				"elementId": "EYU2LhvULtLtUsVpHtrMM",
				"gap": 8.2289394107911,
				"focus": 0.038462699607583604
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
					138.27336347498607,
					108.55682493251027
				]
			]
		},
		{
			"type": "arrow",
			"version": 851,
			"versionNonce": 1733505870,
			"isDeleted": false,
			"id": "IbQrATLSrZrsY1jmduXYn",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 448.11930857764355,
			"y": 950.6324333177229,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 410.1783861683474,
			"height": 999.0455551307496,
			"seed": 1888421629,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1718685443711,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "bmqxqfle9vhLwKzPQ1Tnw",
				"gap": 1.75323486328125,
				"focus": 0.6185398483979183
			},
			"endBinding": {
				"elementId": "yOIKhkwYdk4pM4M2t9bgi",
				"gap": 10.807218131488526,
				"focus": -0.28633672747186967
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
					73.06373596191406,
					-75.9982681274414
				],
				[
					40.78498840332031,
					-581.8823658635711
				],
				[
					-107.52685546875,
					-918.0191040039062
				],
				[
					-337.11465020643334,
					-999.0455551307496
				]
			]
		},
		{
			"type": "arrow",
			"version": 47,
			"versionNonce": 1031256210,
			"isDeleted": false,
			"id": "sOLlucTFCZ4B9cVkeGCYD",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 140.56765757666707,
			"y": 946.1764671345404,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 109.61433410644523,
			"height": 0.174560546875,
			"seed": 2049810493,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "VDE0fR61"
				}
			],
			"updated": 1718685335293,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "EYU2LhvULtLtUsVpHtrMM",
				"gap": 3.4705246478955587,
				"focus": 0.041722298157483795
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
					109.61433410644523,
					0.174560546875
				]
			]
		},
		{
			"type": "text",
			"version": 3,
			"versionNonce": 1810979869,
			"isDeleted": false,
			"id": "VDE0fR61",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 185.16483317481152,
			"y": 933.7637474079779,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 20.41998291015625,
			"height": 25,
			"seed": 331067827,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676208877,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "no",
			"rawText": "no",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "sOLlucTFCZ4B9cVkeGCYD",
			"originalText": "no",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "rectangle",
			"version": 97,
			"versionNonce": 764604573,
			"isDeleted": false,
			"id": "bmqxqfle9vhLwKzPQ1Tnw",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 257.42900096045605,
			"y": 878.933196260517,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 188.93707275390625,
			"height": 137.16835021972656,
			"seed": 1553421907,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 3
			},
			"boundElements": [
				{
					"type": "text",
					"id": "YbEY5aHP"
				},
				{
					"id": "IbQrATLSrZrsY1jmduXYn",
					"type": "arrow"
				}
			],
			"updated": 1718676195793,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 55,
			"versionNonce": 1764532765,
			"isDeleted": false,
			"id": "YbEY5aHP",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 270.0276032553779,
			"y": 922.5173713703803,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 163.7398681640625,
			"height": 50,
			"seed": 253542579,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676189357,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "list의 다음 node를\nmalloc",
			"rawText": "list의 다음 node를 malloc",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "bmqxqfle9vhLwKzPQ1Tnw",
			"originalText": "list의 다음 node를 malloc",
			"lineHeight": 1.25,
			"baseline": 42
		},
		{
			"type": "arrow",
			"version": 41,
			"versionNonce": 1207442770,
			"isDeleted": false,
			"id": "CXp21EzAiSoIcYuGooOGn",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 5.801638799010231,
			"y": 1022.5259444069061,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 4.492314330417891,
			"height": 133.85204122033383,
			"seed": 1008225245,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"type": "text",
					"id": "Cr05Mcr6"
				}
			],
			"updated": 1718685335294,
			"link": null,
			"locked": false,
			"startBinding": {
				"elementId": "EYU2LhvULtLtUsVpHtrMM",
				"gap": 3.6151501748963284,
				"focus": 0.017282497704625557
			},
			"endBinding": {
				"elementId": "y5JHn7C6",
				"gap": 15.75202037855582,
				"focus": 0.0587566452662958
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
					4.492314330417891,
					133.85204122033383
				]
			]
		},
		{
			"type": "text",
			"version": 4,
			"versionNonce": 655200125,
			"isDeleted": false,
			"id": "Cr05Mcr6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -7.0516661538017615,
			"y": 1077.0492375153112,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 31.179962158203125,
			"height": 25,
			"seed": 1814692531,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676218106,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "yes",
			"rawText": "yes",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "CXp21EzAiSoIcYuGooOGn",
			"originalText": "yes",
			"lineHeight": 1.25,
			"baseline": 17
		},
		{
			"type": "ellipse",
			"version": 80,
			"versionNonce": 798750803,
			"isDeleted": false,
			"id": "y5JHn7C6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -128.5538939370049,
			"y": 1172.083169247489,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 268.22265625,
			"height": 156,
			"seed": 1939642899,
			"groupIds": [],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [
				{
					"id": "CXp21EzAiSoIcYuGooOGn",
					"type": "arrow"
				},
				{
					"type": "text",
					"id": "LJ7mqdQj"
				}
			],
			"updated": 1718676280577,
			"link": "[[microshell-flowchart.excalidraw]]",
			"locked": false
		},
		{
			"type": "text",
			"version": 62,
			"versionNonce": 274004435,
			"isDeleted": false,
			"id": "LJ7mqdQj",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -56.05353310726717,
			"y": 1199.9288403149383,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 123.55987548828125,
			"height": 100,
			"seed": 152786131,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1718676251779,
			"link": null,
			"locked": false,
			"fontSize": 20,
			"fontFamily": 1,
			"text": "end\nmicroshell에게\nparse_list를\n넘긴다",
			"rawText": "end\nmicroshell에게 parse_list를 넘긴다",
			"textAlign": "center",
			"verticalAlign": "middle",
			"containerId": "y5JHn7C6",
			"originalText": "end\nmicroshell에게 parse_list를 넘긴다",
			"lineHeight": 1.25,
			"baseline": 92
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
		"scrollX": 1608.6838951655775,
		"scrollY": 466.7097751697986,
		"zoom": {
			"value": 0.55
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