# NIPs

NIPs stand for **Nostr Implementation Possibilities**. They exist to document what MUST, what SHOULD and what MAY be implemented by [Nostr](https://github.com/fiatjaf/nostr)-compatible _relay_ and _client_ software.

- NIP-01：基本协议流程描述
- NIP-02：联系人列表和昵称
- NIP-03：事件的OpenTimestamps证明
- NIP-04：加密的直接消息
- NIP-05：将Nostr键映射到基于DNS的Internet标识符
- NIP-06：基于助记种子短语的基本密钥派生
- NIP-07：Web浏览器的window.nostr功能
- NIP-08：处理提及
- NIP-09：事件删除
- NIP-10：客户端在文本事件中使用e和p标签的约定
- NIP-11：中继器信息文件
- NIP-12：通用标签查询
- NIP-13：工作证明
- NIP-14：文本事件中的主题标签
- NIP-15：存储事件通知结束
- NIP-16：事件处理
- NIP-19：bech32编码实体
- NIP-20：命令结果
- NIP-21：nostr：URL方案
- NIP-22：事件创建_at限制
- NIP-25：反应
- NIP-26：委托事件签名
- NIP-28：公共聊天
- NIP-33：参数化可替换事件
- NIP-36：敏感内容
- NIP-40：过期时间戳
- NIP-42：客户端向中继器的身份验证
- NIP-50：关键字过滤器
- NIP-56：报告
- NIP-65：中继器列表元数据

## Event Kinds

| kind          | description                      | NIP                     |
| ------------- | -------------------------------- | ----------------------- |
| 0             | Metadata                         | [1](01.md), [5](05.md)  |
| 1             | Short Text Note                  | [1](01.md)              |
| 2             | Recommend Relay                  | [1](01.md)              |
| 3             | Contacts                         | [2](02.md)              |
| 4             | Encrypted Direct Messages        | [4](04.md)              |
| 5             | Event Deletion                   | [9](09.md)              |
| 7             | Reaction                         | [25](25.md)             |
| 40            | Channel Creation                 | [28](28.md)             |
| 41            | Channel Metadata                 | [28](28.md)             |
| 42            | Channel Message                  | [28](28.md)             |
| 43            | Channel Hide Message             | [28](28.md)             |
| 44            | Channel Mute User                | [28](28.md)             |
| 45-49         | Public Chat Reserved             | [28](28.md)             |
| 1984          | Reporting                        | [56](56.md)             |
| 10002         | Relay List Metadata              | [65](65.md)             |
| 22242         | Client Authentication            | [42](42.md)             |
| 1000-9999     | Regular Events                   | [16](16.md)             |
| 10000-19999   | Replaceable Events               | [16](16.md)             |
| 20000-29999   | Ephemeral Events                 | [16](16.md)             |
| 30000-39999   | Parameterized Replaceable Events | [33](33.md)             |



## Message types

### Client to Relay
| type  | description                                         | NIP         |
|-------|-----------------------------------------------------|-------------|
| EVENT | used to publish events                              | [1](01.md)  |
| REQ   | used to request events and subscribe to new updates | [1](01.md)  |
| CLOSE | used to stop previous subscriptions                 | [1](01.md)  |
| AUTH  | used to send authentication events                  | [42](42.md) |

### Relay to Client
| type   | description                                             | NIP         |
|--------|---------------------------------------------------------|-------------|
| EVENT  | used to send events requested to clients                | [1](01.md)  |
| NOTICE | used to send human-readable messages to clients         | [1](01.md)  |
| EOSE   | used to notify clients all stored events have been sent | [15](15.md) |
| OK     | used to notify clients if an EVENT was successuful      | [20](20.md) |
| AUTH   | used to send authentication challenges                  | [42](42.md) |

Please update these lists when proposing NIPs introducing new event kinds.

When experimenting with kinds, keep in mind the classification introduced by [NIP-16](16.md).

## Standardized Tags

| name       | value                   | other parameters  | NIP                      |
| ---------- | ----------------------- | ----------------- | ------------------------ |
| e          | event id (hex)          | relay URL, marker | [1](01.md), [10](10.md)  |
| p          | pubkey (hex)            | relay URL         | [1](01.md)               |
| r          | a reference (URL, etc)  |                   | [12](12.md)              |
| t          | hashtag                 |                   | [12](12.md)              |
| g          | geohash                 |                   | [12](12.md)              |
| nonce      | random                  |                   | [13](13.md)              |
| subject    | subject                 |                   | [14](14.md)              |
| d          | identifier              |                   | [33](33.md)              |
| expiration | unix timestamp (string) |                   | [40](40.md)              |

## Criteria for acceptance of NIPs

1. They should be implemented in at least two clients and one relay -- when applicable.
2. They should make sense.
3. They should be optional and backwards-compatible: care must be taken such that clients and relays that choose to not implement them do not stop working when interacting with the ones that choose to.
4. There should be no more than one way of doing the same thing.
5. Other rules will be made up when necessary.

## License

All NIPs are public domain.
