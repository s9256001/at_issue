玩家手動一次同時送約 14 筆電網 CL_HIT, log 顯示 "behavior.handleWeaponMultiFish: duplicate fishID"
```json
{
  "_index": "go-gcp-at-ab3-2023.01.29",
  "_type": "_doc",
  "_id": "ayWQ_oUBEDNtuxDsX98-",
  "_version": 1,
  "_score": null,
  "_source": {
    "@timestamp": "2023-01-29T17:25:47.977Z",
    "ecs": {
      "version": "1.6.0"
    },
    "host": {
      "name": "ab3-gameserver-v3-6944484ff7-kg9xf"
    },
    "Level": "error",
    "req": {
      "BetMultiple": 1,
      "ShootTime": 1675013146706,
      "FishIDs": [
        313,
        314,
        315,
        313,
        314,
        315,
        313,
        314,
        315,
        320,
        319,
        0,
        312,
        0,
        318,
        0,
        309,
        313,
        314,
        315,
        320,
        0,
        319,
        0,
        312,
        0,
        318,
        0,
        309
      ],
      "BuffFishIDs": [
        313,
        314,
        315,
        313,
        314,
        315,
        313,
        314,
        315,
        320,
        319,
        0,
        312,
        0,
        318,
        0,
        309,
        313,
        314,
        315,
        320,
        0,
        319,
        0,
        312,
        0,
        318,
        0,
        309
      ],
      "WeaponType": 2,
      "ProtoName": "CL_HIT",
      "SeatID": 1
    },
    "Msg": "behavior.handleWeaponMultiFish: duplicate fishID",
    "from": "logic",
    "roomID": "uwZFp2G0q",
    "session": "h6M6CjKMM",
    "roundCode": "AB3m1650815m1m1",
    "log": {
      "offset": 946532,
      "file": {
        "path": "/var/log/gs/ab3.log"
      }
    },
    "gameCode": "AB3",
    "input": {
      "type": "log"
    },
    "agent": {
      "version": "8.0.0",
      "ephemeral_id": "418bfafd-66b5-489e-85b1-93d4a8879ba7",
      "id": "123521bd-d9f7-48f3-a5fd-4cb309f35fa4",
      "name": "ab3-gameserver-v3-6944484ff7-kg9xf",
      "type": "filebeat"
    }
  },
  "fields": {
    "@timestamp": [
      "2023-01-29T17:25:47.977Z"
    ]
  },
  "highlight": {
    "Msg": [
      "@kibana-highlighted-field@behavior.handleWeaponMultiFish: duplicate fishID@/kibana-highlighted-field@"
    ],
    "Level": [
      "@kibana-highlighted-field@error@/kibana-highlighted-field@"
    ],
    "from": [
      "@kibana-highlighted-field@logic@/kibana-highlighted-field@"
    ]
  },
  "sort": [
    1675013147977000000
  ]
}
```
該玩家 log 也有 "Seat.CheckFishDetail: compSeatCycle.Bet != sumBet"
```json
{
  "_index": "go-gcp-at-ab3-2023.01.29",
  "_type": "_doc",
  "_id": "aiWK_oUBEDNtuxDsP7CJ",
  "_version": 1,
  "_score": null,
  "_source": {
    "@timestamp": "2023-01-29T17:19:03.863Z",
    "host": {
      "name": "ab3-gameserver-v1-96b5f6d85-kc25x"
    },
    "agent": {
      "type": "filebeat",
      "version": "8.0.0",
      "ephemeral_id": "d9899866-1320-4885-bac9-2e396e9233d3",
      "id": "3f8ad7ca-c935-4529-b5cf-440c9d804cf1",
      "name": "ab3-gameserver-v1-96b5f6d85-kc25x"
    },
    "session": "h6McWIXTH",
    "roundCode": "AB3m1650712m1m1",
    "cycleBet": 262,
    "roomID": "uwZFNX7mE",
    "ecs": {
      "version": "1.6.0"
    },
    "input": {
      "type": "log"
    },
    "log": {
      "offset": 92615,
      "file": {
        "path": "/var/log/gs/ab3.log"
      }
    },
    "Level": "error",
    "from": "logic",
    "gameCode": "AB3",
    "sumBet": 3883,
    "Msg": "Seat.CheckFishDetail: compSeatCycle.Bet != sumBet"
  },
  "fields": {
    "@timestamp": [
      "2023-01-29T17:19:03.863Z"
    ]
  },
  "highlight": {
    "Msg": [
      "@kibana-highlighted-field@Seat.CheckFishDetail: compSeatCycle.Bet != sumBet@/kibana-highlighted-field@"
    ],
    "Level": [
      "@kibana-highlighted-field@error@/kibana-highlighted-field@"
    ],
    "from": [
      "@kibana-highlighted-field@logic@/kibana-highlighted-field@"
    ]
  },
  "sort": [
    1675012743863000000
  ]
}
```
判斷該玩家竄改 CL_HIT 封包, 使用一般子彈擊中多隻魚
造成細單由 hit 數算出的 bet 與實際 bet 對不起來
但由於數學有擋只處理第一條魚, 所以 rtp 會正常
