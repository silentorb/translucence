---
title: Translucence
---
Translucence is a collection of interconnected Bible articles. A core goal is to present modular arguments about Biblical truths — reusable claims and supporting pieces that link together, rather than one-off essays.

```tome-block
{
  "componentId": "tome-query.block",
  "data": {
    "version": 1,
    "reactFlow": {
      "nodes": [
        {
          "id": "in",
          "type": "input",
          "position": { "x": 0, "y": 200 },
          "data": { "inputValues": {} }
        },
        {
          "id": "corpus",
          "type": "corpus",
          "position": { "x": 180, "y": 200 },
          "data": { "inputValues": { "id": "page" } }
        },
        {
          "id": "hopMembers",
          "type": "traverse",
          "position": { "x": 220, "y": 0 },
          "data": {
            "inputValues": {
              "association": "01KZXT3MS0083H8RXPW78QZ0TN",
              "direction": 0
            }
          }
        },
        {
          "id": "hopHubs",
          "type": "traverse",
          "position": { "x": 220, "y": 120 },
          "data": {
            "inputValues": {
              "association": "01KZXT3MS0083H8RXPW78QZ0TN",
              "direction": 1
            }
          }
        },
        {
          "id": "exceptMembers",
          "type": "except",
          "position": { "x": 480, "y": 200 },
          "data": { "inputValues": {} }
        },
        {
          "id": "exceptHubs",
          "type": "except",
          "position": { "x": 700, "y": 200 },
          "data": { "inputValues": {} }
        },
        {
          "id": "colHome",
          "type": "column",
          "position": { "x": 220, "y": 280 },
          "data": { "inputValues": { "name": "id" } }
        },
        {
          "id": "litHome",
          "type": "literal",
          "position": { "x": 220, "y": 360 },
          "data": { "inputValues": { "value": "01KZXT3MRP5GXYXCSRHKF302BG" } }
        },
        {
          "id": "eqHome",
          "type": "equals",
          "position": { "x": 440, "y": 320 },
          "data": { "inputValues": {} }
        },
        {
          "id": "filterHome",
          "type": "filter",
          "position": { "x": 660, "y": 320 },
          "data": { "inputValues": {} }
        },
        {
          "id": "exceptHome",
          "type": "except",
          "position": { "x": 920, "y": 200 },
          "data": { "inputValues": {} }
        },
        {
          "id": "colArchive",
          "type": "column",
          "position": { "x": 220, "y": 440 },
          "data": { "inputValues": { "name": "id" } }
        },
        {
          "id": "litArchive",
          "type": "literal",
          "position": { "x": 220, "y": 520 },
          "data": { "inputValues": { "value": "01KZXT3MS0JYENYDDZXWHGDAEJ" } }
        },
        {
          "id": "eqArchive",
          "type": "equals",
          "position": { "x": 440, "y": 480 },
          "data": { "inputValues": {} }
        },
        {
          "id": "filterArchive",
          "type": "filter",
          "position": { "x": 660, "y": 480 },
          "data": { "inputValues": {} }
        },
        {
          "id": "exceptArchive",
          "type": "except",
          "position": { "x": 1140, "y": 200 },
          "data": { "inputValues": {} }
        },
        {
          "id": "sort",
          "type": "sort",
          "position": { "x": 1360, "y": 200 },
          "data": {
            "inputValues": {
              "column": "title",
              "direction": "asc"
            }
          }
        },
        {
          "id": "project",
          "type": "project",
          "position": { "x": 1580, "y": 200 },
          "data": { "inputValues": { "columns": "id" } }
        },
        {
          "id": "out",
          "type": "output",
          "position": { "x": 1800, "y": 200 },
          "data": { "inputValues": {} }
        }
      ],
      "edges": [
        {
          "id": "e_in_corpus",
          "source": "in",
          "target": "corpus",
          "sourceHandle": "value",
          "targetHandle": "collection"
        },
        {
          "id": "e_in_hopMembers",
          "source": "corpus",
          "target": "hopMembers",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_in_hopHubs",
          "source": "corpus",
          "target": "hopHubs",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_in_exceptMembers",
          "source": "corpus",
          "target": "exceptMembers",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_excl_members",
          "source": "hopMembers",
          "target": "exceptMembers",
          "sourceHandle": "collection",
          "targetHandle": "exclude"
        },
        {
          "id": "e_keep_exceptHubs",
          "source": "exceptMembers",
          "target": "exceptHubs",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_excl_hubs",
          "source": "hopHubs",
          "target": "exceptHubs",
          "sourceHandle": "collection",
          "targetHandle": "exclude"
        },
        {
          "id": "e_colHome_eq",
          "source": "colHome",
          "target": "eqHome",
          "sourceHandle": "value",
          "targetHandle": "left"
        },
        {
          "id": "e_litHome_eq",
          "source": "litHome",
          "target": "eqHome",
          "sourceHandle": "value",
          "targetHandle": "right"
        },
        {
          "id": "e_in_filterHome",
          "source": "corpus",
          "target": "filterHome",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_eqHome_filter",
          "source": "eqHome",
          "target": "filterHome",
          "sourceHandle": "value",
          "targetHandle": "predicate"
        },
        {
          "id": "e_keep_exceptHome",
          "source": "exceptHubs",
          "target": "exceptHome",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_excl_home",
          "source": "filterHome",
          "target": "exceptHome",
          "sourceHandle": "collection",
          "targetHandle": "exclude"
        },
        {
          "id": "e_colArchive_eq",
          "source": "colArchive",
          "target": "eqArchive",
          "sourceHandle": "value",
          "targetHandle": "left"
        },
        {
          "id": "e_litArchive_eq",
          "source": "litArchive",
          "target": "eqArchive",
          "sourceHandle": "value",
          "targetHandle": "right"
        },
        {
          "id": "e_in_filterArchive",
          "source": "corpus",
          "target": "filterArchive",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_eqArchive_filter",
          "source": "eqArchive",
          "target": "filterArchive",
          "sourceHandle": "value",
          "targetHandle": "predicate"
        },
        {
          "id": "e_keep_exceptArchive",
          "source": "exceptHome",
          "target": "exceptArchive",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_excl_archive",
          "source": "filterArchive",
          "target": "exceptArchive",
          "sourceHandle": "collection",
          "targetHandle": "exclude"
        },
        {
          "id": "e_sort",
          "source": "exceptArchive",
          "target": "sort",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_project",
          "source": "sort",
          "target": "project",
          "sourceHandle": "collection",
          "targetHandle": "collection"
        },
        {
          "id": "e_out",
          "source": "project",
          "target": "out",
          "sourceHandle": "collection",
          "targetHandle": "value"
        }
      ]
    }
  }
}
```
