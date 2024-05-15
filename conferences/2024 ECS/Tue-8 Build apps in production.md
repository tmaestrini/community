---
Conference: ECS24
Date: 15.05.2024 17:20
Speaker: Garry Trinder
Type: Personal Notes
Categories: Development
---

# Build apps that don't fail in production

## What are relisient apps?

An app is resilient if it conntinues to carry out its mission in the face of adversity. It doesn't lose data.
Resilience assumes that adverse conditions **will** occur – it's not a tick box.
**Resilience is a combination of availability, capacity, interoperability, performance, reliability, robustness, safety, security and usability.**

As a fact, cloud APIs fail – it's not a mattor of _if_, it's _when_. At the moment they fail: how do you know what is going to _happen_? (How) will the app _recover_? How can we _test_ all these questions?

APIs that you don't own are pretty hard (or impossible) to test – along the fact, that nobody wants to pay for testing. 
Although there are "standards" for (return values of) APIs – each and every API behaves completely differently from the other: some return `429`, others `403` or ... as HTTP error feedback.
Often, proper API documentation that handles returns and failures is missing completely. We need (independent) tools that provides support in testing APIs – to build apps that can handle API failures and errors accordingly.

## Dev Proxy
Dev Proxy helps to build resilient apps on M365 – and leads to improvements of robustness, performance and security of an app:
[https://aka.ms/devproxy](https://aka.ms/devproxy)

Dev Proxy supports _any_ HTTP API and can be run against _any_ app and _any_ plattform (and _any_ tech stack).
We can to "provoke"...
- random errors
- latency
- throttling

... and test behaviours like...
- `$select` guidance 
- throttling

... as well as improve security (for Microsoft Graph calls: detect minimum required permissions or detect over consented applications).

### Using DevProxy

Start DevProxy by typing `devproxy` in Terminal.

```bash
$ devproxy
8 error responses loaded from /opt/homebrew/Cellar/dev-proxy/0.17.1/devproxy-errors.json
Listening on 127.0.0.1:8000...
Hotkeys: issue (w)eb request, (r)ecord, (s)top recording, (c)lear screen
Press CTRL+C to stop Dev Proxy
```

In the very well-documented documentation, follow the [«How-To» guidelines](https://learn.microsoft.com/en-us/microsoft-cloud/dev/dev-proxy/how-to/overview) to get familiar with the tool.