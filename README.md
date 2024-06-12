# NODEPP-TOR-CLIENT

A Simple TOR client for NodePP

## Usage 
```cpp
#include <nodepp/nodepp.h>
#include <http.h>

using namespace nodepp;

void onMain() {

    tor_fetch_t args;
    args.timeout = 0;
    args.methodo = "GET";
    args.url     = "http://check.torproject.org/";
    args.headers = header_t({
        { "host", "check.torproject.org" }
    });

    tor::http::fetch( args )

    .then([]( http_t cli ){
        console::log( cli.read() );
    })

    .fail([]( except_t err ){
        console::log(err);
    });

}
```

## Build & Run
- 🐧: `g++ -o main main.cpp -I ./include ; ./main`
- 🪟: `g++ -o main main.cpp -I ./include -lws2_32 ; ./main`

## License

**Nodepp** is distributed under the MIT License. See the LICENSE file for more details.
