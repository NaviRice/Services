<img src="logo_small.png" align="right" />

# NaviRice Services
NaviRice backend services written in C++

## What's inside?

| Services            | Location     |
| ------------------- | -----------: |
| Common Data Service | `/common`    |
| Rendering Service   | `/rendering` |

| Examples                   | Location                           |
| -------------------------- | ---------------------------------: |
| Android App Client         | `/common/src/test/client_test.cpp` |
| Renderer Bridge            | `/renderer_bridge`                 |

## Getting Started

### Prerequisites

- [Git](https://git-scm.com/download) v2.13.6
- [cmake](https://cmake.org/download) v3.10.2
- [Protocol Buffers](https://github.com/google/protobuf) v3.5.0

### Setting up git submodules

Before moving forward, please remember to initialize and pull all the git submodules by running the following commands in the terminal:

```bash
git submodule init
git submodule update
```

### Building from source

To compile the backend services, run the following commands in the terminal:

```bash
mkdir build
cd build
cmake ..
```

### Installation

To install the generated libraries and public headers, run the following command in the terminal:

```bash
sudo make install
```

You should see the following output after installing all the services successfully:

```
[ 30%] Built target proto
[ 46%] Built target common
[ 60%] Built target client
[ 76%] Built target service
[ 90%] Built target server
[100%] Built target renderingService
Install the project...
-- Install configuration: ""
-- Up-to-date: /usr/local/lib/librenderingService.dylib
-- Up-to-date: /usr/local/include/navirice/Step.h
-- Up-to-date: /usr/local/include/navirice/InitService.h
```

### Running

#### Launching Server

To start the example server, run the following command in the terminal:

```bash
./bin/server 0.0.0.0 8000
```

You should see the following output in the terminal:

```
Waiting for connection
```

#### Launching Service

To start the example service, run the following command in the terminal:

```bash
./bin/service 0.0.0.0 8000
```

You should see the following output in the terminal:

```
[RENDERING][1] Service started.
```

#### Launching Renderer Bridge

To start the example renderer bridge, run the following command in the terminal:

```bash
./bin/renderer 0.0.0.0 8000
```

You should see the following output in the terminal:

```
00:02:52 [RENDERING][1] Service started.
```

#### Connecting to a Server / Service

To connect to a server or a service, run the following command in the terminal:

```bash
./bin/client 0.0.0.0 8000
```


You should be promoted to enter the current step if connected to the server / service successfully:

```bash
Connect established.
Please enter x(double) y(double) description(string) icon(string):
```

Here is a sample input:

```
71.207 -31.03 TestDescription TestIconID
```

Here is the corresponding outputs:

##### Client
```
x: 71.207
y: -31.03
description: "TestDescription"
icon: "TestIconID"

00:12:05 [HEAD_TRACKING][NaviRices 1] CURRENT_STEP
```

##### Renderer
```
00:09:03 [RENDERING][1] Accept connection
[Step x=71.207000 y=-31.030000 description=TestDescription step=TestIconID]
00:12:05 [RENDERING][1] CURRENT_STEP
```

## Deployment

## Contributing
When contributing to this repository, please first discuss the change you wish to make via issue, email, or Facebook group chat with the owners of this repository before making a change.

1. Ensure any install or build dependencies are removed before the end of the layer when doing a build.

2. Update the README.md with details of changes to the interface, this includes new environment variables, exposed ports, useful file locations and container parameters.

3. Increase the version numbers in any examples files and the README.md to the new version that this Pull Request would represent. The versioning scheme we use is SemVer.

4. You may merge the Pull Request in once you have the sign-off of two other developers, or if you do not have permission to do that, you may request the second reviewer to merge it for you.

## Authors

- **Yang Liu** - *Initial work* - [byliuyang](https://github.com/byliuyang)
- **Can Alper** - *Optimized server performance* - [calper-ql](https://github.com/calper-ql)
- **Alex Gaines** - *Interfaced rendering service with renderer* - [roboman2444](https://github.com/roboman2444)
- **Binam Kayastha** - *To do some work in the future* - [binamkayastha](https://github.com/binamkayastha)

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
