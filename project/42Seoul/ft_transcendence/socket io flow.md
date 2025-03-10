---

excalidraw-plugin: parsed
tags: [excalidraw]

---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
game lobby ^NQZlU43I

queue ^a9OjiCKZ

tournament ^jZRAhbXO

큐에서 뒤로가기하면 들어있던 큐에서는 강퇴당한다. ^ubTXUtsG

pong game ^V8sH2IQY

게임에서 뒤로 가기를 누르면 기권 처리되고 토너먼트 페이지로도 다시 되돌아갈 수 없으며, 바로 게임 로비 페이지로 되돌아간다. ^3chfoqjg

make new queue ^LjNFwvFC

토너먼트 끝 ^EqRS4kEx

아래의 모든 페이지에서 메인 페이지, 마이 페이지, 대시보드로의 링크 버튼은 비활성화된다. ^lABZcSTr

connect ^lvZCxrDG

other page ^Sl1u97eo

disconnect ^wRIowL6e

event.on: room_list ^fO2x3u63

서버는 connect 되자마자 바로 room_list 이벤트를 emit한다. ^wStg6XSK

게임 관련 페이지가 아닌 페이지로 넘어가면 disconnect 된다. ^L5XXIEFJ

event.emit: make_room ^BL7ZhRa2

make queue 버튼을 누른다면 ^hd5aEdWu

X : make_room 이벤트를 실행시킨 당사자는 room_list 이벤트를 더 이상 받지 않는다.

방에 참여하지 않은 사람에게는 방 명단에 변동이 있으므로 서버가 room_list 이벤트를 emit한다. ^dCHZHql8

직접 새로운 방을 만든 경우
{room_name: string, room_limit: int} ^6SpOp9Ie

event.emit:enter_room ^uBu2dWAw

X : enter_room 이벤트를 실행시킨 당사자는 room_list 이벤트를 더 이상 받지 않는다.

방에 참여하지 않은 사람에게는 방 명단에 변동이 있으므로 서버가 room_list 이벤트를 emit한다. ^z5ai7dFJ

다른 사람이 만든 방으로 들어간 경우
{room_id: string} ^4fF15NUx

event.emit: leave_room ^yLoXzsze

event.on: room_changed ^e0YN5TOO

방의 현재 상태가 변경되었을 때 서버는 이 이벤트를 emit한다. ^YqTujdIp

방에 들어가 있는 상태 ^PzEO59wD

방에서 나갈때 서버로부터 room_list 이벤트를 emit 받는다. 이후로 지속적으로 room_list 이벤트를 emit 받는다. ^nmN3iDYQ

직접 큐를 안 만들고 다른 사람이 만들어놓은 큐로 들어가는 경우 ^7loaJ3hS

검은색: page flow ^NefFfA2a

주황색 : socket io event flow ^DDm64fT3

%%
## Drawing
```compressed-json
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=
```
%%