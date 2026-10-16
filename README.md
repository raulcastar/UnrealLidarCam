# UnrealLidarCam

A lidar for Unreal Engine 5 with a free beam pattern (horizontal and vertical
aperture, beams per axis), measured on the GPU or by line traces, streamed to
ROS over TCP.

![Lidar point cloud of a crater and rocks while the rover drives](docs/images/lidar.gif)

*Scans of a crater and two rocks while the rover drives in GNC Moon Simulator
(rover frame, coloured by height).*

Part of [GNC Moon Simulator](https://github.com/raulcastar/GNC-Moon-Simulator):
its `component_lidar` node publishes the scans as a `PointCloud2` on
`lidar/points` (port 3007).

## Requirements

Unreal Engine 5.7 on Windows (the version it is developed and tested with).
Building from source also needs Visual Studio 2022 with the *Game development
with C++* workload.

## Install

- **Prebuilt (UE 5.7, Win64):** download `UnrealLidarCam-<version>-UE5.7-Win64.zip`
  from [Releases](https://github.com/raulcastar/UnrealLidarCam/releases) and extract it
  into `<YourProject>/Plugins/`.
- **From source:** clone this repository into `<YourProject>/Plugins/UnrealLidarCam`,
  open the project and answer **Yes** to rebuild the module.

Then check it is enabled under *Edit → Plugins → Project → Other*.

## Use

1. Add an **Unreal Lidar Cam** component to the rover and attach it under a
   camera (it scans along that camera's view).
2. Set the aperture and beams in *Details → Lidar*.
3. Press Play: scans go to `127.0.0.1:3007`.

## Dependencies

None to build or run: only engine modules. It stamps its data with the shared
simulation time (its own copy of `GncSimTime.h`); add
[UnrealSimClock](https://github.com/raulcastar/UnrealSimClock) so ROS gets `/clock` on the same time base.

## Docs

| | |
|---|---|
| [Setup in detail](docs/setup.md) | Attaching it, following a camera |
| [Settings and scan modes](docs/settings.md) | Every setting; GPU and CPU modes |
| [In ROS](docs/ros.md) | The published point cloud |
| [Wire format](docs/wire-format.md) | The TCP packet layout |
| [Making a release](docs/release.md) | Building the prebuilt zip for GitHub releases |

## License

[MIT](LICENSE), © 2026 Raul Castilla Arquillo.
