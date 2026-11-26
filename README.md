# Trans-RoutE-Townish (transroutownish) :small_blue_diamond: Urban bus routing microservice prototype :small_blue_diamond: <img src="https://vlang.io/img/v-logo.png" style="border:0;width:32px" alt="V" />

**A daemon written in V, designed and intended to be run as a microservice,
<br />implementing a simple urban bus routing prototype**

**Rationale:** This project is a *direct* **[V](https://vlang.io "The V Programming Language")** port of the earlier developed **Urban bus routing microservice prototype**, written in C99 using **[libsoup-3.0](https://libsoup.gnome.org/libsoup-3.0/ "Soup &ndash; 3.0: HTTP client/server library for GNOME")** web client/server library, and tailored to be run as a microservice in a Docker container. The following description of the underlying architecture and logics has been taken **[from here](https://github.com/rgolubtsov/transroutownish-proto-bus-libsoup/blob/main/README.md)** almost as is, without any principal modifications or adjustment.

Consider an IoT system that aimed at planning and forming a specific bus route for a hypothetical passenger. One crucial part of such system is a **module**, that is responsible for filtering bus routes between two arbitrary bus stops where a direct route is actually present and can be found easily. Imagine there is a fictional urban public transportation agency that provides a wide series of bus routes, which covered large city areas, such that they are consisting of many bus stop points in each route. Let's name this agency **Trans-RoutE-Townish Co., Ltd.** or in the Net representation&mdash;**transroutownish.com**, hence the name of the project.

A **module** that is developed in this repo is dedicated to find out quickly, whether there is a direct route in a list of given bus routes between two specified bus stops. By design, it should report back to the IoT system immediately with the result `true` if such a route is found, i.e. it exists in the bus routes list, or `false` otherwise, by producing a simple JSON object like the following:

```json
{
    "from"   : <starting_bus_stop_point>,
    "to"     : <ending_bus_stop_point>,
    "direct" : true
}
```

Values of placeholders `<starting_bus_stop_point>` and `<ending_bus_stop_point>` above are bus stop IDs: unique decimal positive integer numbers, taken right from the inputs passed to this module.

A bus routes list is a plain text file where each route has its own unique ID (decimal positive integer number) and a sequence of its bus stop IDs. Each route occupies only one line in this file, so that they are all representing something similar to a list&mdash;the list of routes. The first number in a route is always its own ID. Other consequent numbers after it are simply IDs of bus stops in this route, up to the end of line. All IDs in each route are separated by whitespace (spaces or tabs) but not a newline character.

There are some constraints:
1. Routes are considered not to be a round trip journey, that is they are operated in the forward direction only.
2. All IDs (of routes and bus stops) must be represented by decimal positive integer numbers, in the range `1 .. 2,147,483,647`.
3. Any bus stop ID may occure in the current route only once, but it might be presented in any other route too.

The list of routes is usually mentioned throughout the source code of this module as a **routes data store**.

**TBD** :cd:

---

**WIP** :dvd:
