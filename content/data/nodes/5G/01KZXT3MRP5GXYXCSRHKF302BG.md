---
title: Translucence
---
Translucence is a collection of interconnected Bible articles. A core goal is to present modular arguments about Biblical truths — reusable claims and supporting pieces that link together, rather than one-off essays.

```json {type="query"}
{
  "version": 1,
  "graph": {
    "nodes": [
      {
        "id": "in",
        "type": "input",
        "inputs": {}
      },
      {
        "id": "corpus",
        "type": "corpus",
        "inputs": {
          "id": "page"
        }
      },
      {
        "id": "hopMembers",
        "type": "traverse",
        "inputs": {
          "association": "01KXBNPNJDENZ9BXN5BYZ7JKPT",
          "direction": 0
        }
      },
      {
        "id": "hopHubs",
        "type": "traverse",
        "inputs": {
          "association": "01KXBNPNJDENZ9BXN5BYZ7JKPT",
          "direction": 1
        }
      },
      {
        "id": "exceptMembers",
        "type": "except",
        "inputs": {}
      },
      {
        "id": "exceptHubs",
        "type": "except",
        "inputs": {}
      },
      {
        "id": "colHome",
        "type": "column",
        "inputs": {
          "name": "id"
        }
      },
      {
        "id": "litHome",
        "type": "literal",
        "inputs": {
          "value": "01KZXT3MRP5GXYXCSRHKF302BG"
        }
      },
      {
        "id": "eqHome",
        "type": "equals",
        "inputs": {}
      },
      {
        "id": "filterHome",
        "type": "filter",
        "inputs": {}
      },
      {
        "id": "exceptHome",
        "type": "except",
        "inputs": {}
      },
      {
        "id": "colArchive",
        "type": "column",
        "inputs": {
          "name": "id"
        }
      },
      {
        "id": "litArchive",
        "type": "literal",
        "inputs": {
          "value": "01KZXT3MS0JYENYDDZXWHGDAEJ"
        }
      },
      {
        "id": "eqArchive",
        "type": "equals",
        "inputs": {}
      },
      {
        "id": "filterArchive",
        "type": "filter",
        "inputs": {}
      },
      {
        "id": "exceptArchive",
        "type": "except",
        "inputs": {}
      },
      {
        "id": "sort",
        "type": "sort",
        "inputs": {
          "column": "title",
          "direction": "asc"
        }
      },
      {
        "id": "project",
        "type": "project",
        "inputs": {
          "columns": "id"
        }
      },
      {
        "id": "out",
        "type": "output",
        "inputs": {}
      }
    ],
    "edges": [
      {
        "id": "e_in_corpus",
        "from": {
          "node": "in",
          "port": "value"
        },
        "to": {
          "node": "corpus",
          "port": "collection"
        }
      },
      {
        "id": "e_in_hopMembers",
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "hopMembers",
          "port": "collection"
        }
      },
      {
        "id": "e_in_hopHubs",
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "hopHubs",
          "port": "collection"
        }
      },
      {
        "id": "e_in_exceptMembers",
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "exceptMembers",
          "port": "collection"
        }
      },
      {
        "id": "e_excl_members",
        "from": {
          "node": "hopMembers",
          "port": "collection"
        },
        "to": {
          "node": "exceptMembers",
          "port": "exclude"
        }
      },
      {
        "id": "e_keep_exceptHubs",
        "from": {
          "node": "exceptMembers",
          "port": "collection"
        },
        "to": {
          "node": "exceptHubs",
          "port": "collection"
        }
      },
      {
        "id": "e_excl_hubs",
        "from": {
          "node": "hopHubs",
          "port": "collection"
        },
        "to": {
          "node": "exceptHubs",
          "port": "exclude"
        }
      },
      {
        "id": "e_colHome_eq",
        "from": {
          "node": "colHome",
          "port": "value"
        },
        "to": {
          "node": "eqHome",
          "port": "left"
        }
      },
      {
        "id": "e_litHome_eq",
        "from": {
          "node": "litHome",
          "port": "value"
        },
        "to": {
          "node": "eqHome",
          "port": "right"
        }
      },
      {
        "id": "e_in_filterHome",
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "filterHome",
          "port": "collection"
        }
      },
      {
        "id": "e_eqHome_filter",
        "from": {
          "node": "eqHome",
          "port": "value"
        },
        "to": {
          "node": "filterHome",
          "port": "predicate"
        }
      },
      {
        "id": "e_keep_exceptHome",
        "from": {
          "node": "exceptHubs",
          "port": "collection"
        },
        "to": {
          "node": "exceptHome",
          "port": "collection"
        }
      },
      {
        "id": "e_excl_home",
        "from": {
          "node": "filterHome",
          "port": "collection"
        },
        "to": {
          "node": "exceptHome",
          "port": "exclude"
        }
      },
      {
        "id": "e_colArchive_eq",
        "from": {
          "node": "colArchive",
          "port": "value"
        },
        "to": {
          "node": "eqArchive",
          "port": "left"
        }
      },
      {
        "id": "e_litArchive_eq",
        "from": {
          "node": "litArchive",
          "port": "value"
        },
        "to": {
          "node": "eqArchive",
          "port": "right"
        }
      },
      {
        "id": "e_in_filterArchive",
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "filterArchive",
          "port": "collection"
        }
      },
      {
        "id": "e_eqArchive_filter",
        "from": {
          "node": "eqArchive",
          "port": "value"
        },
        "to": {
          "node": "filterArchive",
          "port": "predicate"
        }
      },
      {
        "id": "e_keep_exceptArchive",
        "from": {
          "node": "exceptHome",
          "port": "collection"
        },
        "to": {
          "node": "exceptArchive",
          "port": "collection"
        }
      },
      {
        "id": "e_excl_archive",
        "from": {
          "node": "filterArchive",
          "port": "collection"
        },
        "to": {
          "node": "exceptArchive",
          "port": "exclude"
        }
      },
      {
        "id": "e_sort",
        "from": {
          "node": "exceptArchive",
          "port": "collection"
        },
        "to": {
          "node": "sort",
          "port": "collection"
        }
      },
      {
        "id": "e_project",
        "from": {
          "node": "sort",
          "port": "collection"
        },
        "to": {
          "node": "project",
          "port": "collection"
        }
      },
      {
        "id": "e_out",
        "from": {
          "node": "project",
          "port": "collection"
        },
        "to": {
          "node": "out",
          "port": "value"
        }
      }
    ]
  },
  "layout": {
    "in": {
      "x": 0,
      "y": 200
    },
    "corpus": {
      "x": 180,
      "y": 200
    },
    "hopMembers": {
      "x": 220,
      "y": 0
    },
    "hopHubs": {
      "x": 220,
      "y": 120
    },
    "exceptMembers": {
      "x": 480,
      "y": 200
    },
    "exceptHubs": {
      "x": 700,
      "y": 200
    },
    "colHome": {
      "x": 220,
      "y": 280
    },
    "litHome": {
      "x": 220,
      "y": 360
    },
    "eqHome": {
      "x": 440,
      "y": 320
    },
    "filterHome": {
      "x": 660,
      "y": 320
    },
    "exceptHome": {
      "x": 920,
      "y": 200
    },
    "colArchive": {
      "x": 220,
      "y": 440
    },
    "litArchive": {
      "x": 220,
      "y": 520
    },
    "eqArchive": {
      "x": 440,
      "y": 480
    },
    "filterArchive": {
      "x": 660,
      "y": 480
    },
    "exceptArchive": {
      "x": 1140,
      "y": 200
    },
    "sort": {
      "x": 1360,
      "y": 200
    },
    "project": {
      "x": 1580,
      "y": 200
    },
    "out": {
      "x": 1800,
      "y": 200
    }
  }
}
```
