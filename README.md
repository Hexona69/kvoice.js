Before using this package, you confirm your understanding that, by using this package, you are **violating**
- Section 3.2.3 or 3.2.5 of the [*KOOK Software Premission and Service Agreement*](https://www.kookapp.cn/protocol.html), and
- Section *Data Information* or *Abusive Use* of [*KOOK Developer Privacy Policy*](https://developer.kookapp.cn/doc/privacy)

Your KOOK account could face penalty including, but not limited to, 
- **restriction** to the access of developer tools and resources
- **suspension** of user account

Use this package at your own risk. **No warranties** are provided.

---

```typescript
import koice from 'koice';
```

You must have `ffmpeg` in your PATH, or you can specify one

```typescript
const client = new koice('Your KOOK bot token', '/path/to/your/ffmpeg/binary');
```

Connect to WebSocket and retrive RTP URL.

```typescript
client.connectWebSocket("8403799012661514");
```

Start streaming with path to a file or a `stream.readable`;

```typescript
import * as fs from 'fs';
const stream = fs.createReadStream('/path/to/music/file');
await client.startStream(stream);
```

or 

```typescript
await client.startStream('/path/to/music/file');
```

You can also start a ZeroMQ server to be able to stream different files without disconnecting. You can do that by invoking `koice.startServer()` first, then start streaming.

```typescript
await client.startServer();
await client.startStream('/path/to/music/file');
```

And you can also close the ZeroMQ server without stopping the stream, to switch voice channel without streaming again.

```typescript
import * as fs from 'fs';

const stream = fs.createReadStream('/path/to/music/file');

client.connectWebSocket("8591468140337193");
await client.startServer();

await client.startStream(stream);

await delay(1000);

await client.closeServer();
await client.disconnectWebSocket();

client.connectWebSocket("1586400722913705");
await client.startServer();
```

You can refer to [kook-ongaku-play](https://github.com/Hexona69/kook-ongaku-play) for usage of this package in real world application.

---

© 2022 Hexona, [koice.js](https://github.com/Hexona69/koice.js) and [kook-ongaku-play](https://github.com/Hexona69/kook-ongaku-play), released under [the MIT license](https://github.com/Hexona69/koice.js/blob/main/LICENSE).