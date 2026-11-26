# Trans-RoutE-Townish (transroutownish) :small_blue_diamond: Urban bus routing microservice prototype <img src="https://vlang.io/img/v-logo.png" style="border:0;width:32px" alt="V" />

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

Values `<starting_bus_stop_point>` and `<ending_bus_stop_point>` above are bus stop IDs: unique decimal positive integer numbers, taken right from inputs.

**TBD** :cd:

---

**WIP** :dvd:
