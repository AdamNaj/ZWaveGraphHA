# Z-Wave Graph for Home Assistant

This custom panel can display your Z-Wave topology (as available to the system) in Home Assistant (http://www.home-assistant.io) .
Old location: https://gist.github.com/AdamNaj/cbf4d792a22f443fe9d354e4dca4de00


![Sample screenshot](screenshot.png?raw=true "Sample screenshot")

### Requirements
- Home Assistant 0.115+
- For older versions of Home Assistant consider using [this old version of the component](https://gist.github.com/AdamNaj/cbf4d792a22f443fe9d354e4dca4de00)

### Installation

- Copy `zwavegraph3.js`  to `<config dir>/www` directory.
- Configure with config below.
- Restart Home-Assistant.

### Configuration
Add the following to the Home Assistant `configuration.yaml` file:

```yaml
panel_custom:
  - name: zwave-graph-panel
    url_path: zwave-graph
    sidebar_title: Z-Wave Graph
    sidebar_icon: mdi:z-wave
    module_url: /local/zwavegraph3.js
    config:
      # ranker - pick one: network-simplex, tight-tree, longest-path
      ranker: network-simplex
      # edge_visibility - pick one: relevant, all
      edge_visibility: relevant
      # grouping - pick one: z-wave, ungrouped
      grouping: z-wave
```

## Changelog

#### Version 1.0:
- based on the brilliant code by @NigelL - with cosmetic changes mostly about clarity and shaping of nodes based on their function
  https://community.home-assistant.io/t/z-wave-graph-without-the-python
#### Version 2.0: (02 July 2019)
- you can now pan the graph by dragging it
- you can now zoom the graph with your mouse wheel
- the graph initially is scaled to fill the full screen width
- added minimap to visualize which part of the graph you can see at the oment on the screen
- added 2 more tree layouts (click on the top-legend) - they didn't necessarily help me make the graph more manageable for me, but ay be useful to others in their topology
- added the ability to show all node connections if someone wants to see the full picture of their Z-Wave mesh
- fixed the broken new line in the node tooltips
- you can now click on the node to see the entity dialog
#### Version 2.1: (20 September 2019)
- added Tools to graph legends so you can easily navigate to Z-Wave Network Management
- fixed (hopefully) the problem with the graph requiring page reload then navigating to it
#### Version 2.2: (04 October 2019)
- ability to turn off node grouping. Having the nodes grouped requires editing locations defined in the zwcfg_*.cfg
#### Version 2.3: (03 February 2020)
- Graph background reflects theme background color after page reload
- Fixed problem where some removed nodes lingering in the device registry could cause wrong node info card to be displayed after clicking on nodes with higher ids
#### Version 3.0: (21 September 2020)
- restructure to accomodate for a breaking change in Home Assistant 0.115
- default graph ranker, edge visibility and grouping settings are now customizable in configuration.yaml
- move from Gist to GitHub - to enable Pull Requests
#### Version 3.1: (07 October 2020)
- Fix for Javscript Error in Log, blank screen - "Uncaught SyntaxError: Unexpected token '<'" (hopefully)
- Added 'tap' and 'touchstart' event for mobile devices. (Thank you @dennykorsukewitz!)
- Changed the colors of legends and sub legends. #DarkMode (Thank you @dennykorsukewitz!)

## TODO:
- support for theming
- support for HACS