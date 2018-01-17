# mlsp

Multiple Local SSL Proxy. Inspired by [`local-ssl-proxy`](https://github.com/cameronhunter/local-ssl-proxy).

:warning: It's only intended for development usage only! It will show a certificate warning


## Usage

#### Install

```sh
npm install -g mlsp
```

#### Basic usage

```sh
# Starts a proxy from 127.0.0.1:8080 to 127.0.0.1:8081
mlsp --source 8080 --target 8081
```

#### Advanced usage

`mlsp` can be configured to route based on different hostnames given a routing table. For example, the following table:

```json
{
  "service-1.local.foobar.com": {
    "port": "8081"
  },
  "service-2.local.foobar.com": {
    "port": "8082"
  },
  "default": {
    "port": "8080"
  }
}
```

And the following command:
```sh
sudo mlsp --source 443 --routing ./routing_table.json
```

Will start the server on 443 port (default https port), and will route requests based on their hostname. To add such routing, one must also edit `/etc/hosts` to point the given hosts to `127.0.0.1`.
