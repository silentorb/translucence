---
title: Translucence
---
Translucence is a collection of interconnected Bible articles. A core goal is to present modular arguments about Biblical truths — reusable claims and supporting pieces that link together, rather than one-off essays.

```json {type="query"}
{
  "version": 1,
  "graph": {
    "nodes": {
      "in": {
        "id": "in",
        "type": "input",
        "inputs": {}
      },
      "corpus": {
        "id": "corpus",
        "type": "corpus",
        "inputs": {
          "id": "page"
        }
      },
      "hopMembers": {
        "id": "hopMembers",
        "type": "traverse",
        "inputs": {
          "association": "01KXBNPNJDENZ9BXN5BYZ7JKPT",
          "direction": 0
        }
      },
      "hopHubs": {
        "id": "hopHubs",
        "type": "traverse",
        "inputs": {
          "association": "01KXBNPNJDENZ9BXN5BYZ7JKPT",
          "direction": 1
        }
      },
      "exceptMembers": {
        "id": "exceptMembers",
        "type": "except",
        "inputs": {}
      },
      "exceptHubs": {
        "id": "exceptHubs",
        "type": "except",
        "inputs": {}
      },
      "colHome": {
        "id": "colHome",
        "type": "column",
        "inputs": {
          "name": "id"
        }
      },
      "litHome": {
        "id": "litHome",
        "type": "literal",
        "inputs": {
          "value": "01KZXT3MRP5GXYXCSRHKF302BG"
        }
      },
      "eqHome": {
        "id": "eqHome",
        "type": "equals",
        "inputs": {}
      },
      "filterHome": {
        "id": "filterHome",
        "type": "filter",
        "inputs": {}
      },
      "exceptHome": {
        "id": "exceptHome",
        "type": "except",
        "inputs": {}
      },
      "colArchive": {
        "id": "colArchive",
        "type": "column",
        "inputs": {
          "name": "id"
        }
      },
      "litArchive": {
        "id": "litArchive",
        "type": "literal",
        "inputs": {
          "value": "01KZXT3MS0JYENYDDZXWHGDAEJ"
        }
      },
      "eqArchive": {
        "id": "eqArchive",
        "type": "equals",
        "inputs": {}
      },
      "filterArchive": {
        "id": "filterArchive",
        "type": "filter",
        "inputs": {}
      },
      "exceptArchive": {
        "id": "exceptArchive",
        "type": "except",
        "inputs": {}
      },
      "sort": {
        "id": "sort",
        "type": "sort",
        "inputs": {
          "column": "title",
          "direction": "asc"
        }
      },
      "project": {
        "id": "project",
        "type": "project",
        "inputs": {
          "columns": "id"
        }
      },
      "out": {
        "id": "out",
        "type": "output",
        "inputs": {}
      }
    },
    "edges": {
      "e_in_corpus": {
        "from": {
          "node": "in",
          "port": "value"
        },
        "to": {
          "node": "corpus",
          "port": "collection"
        }
      },
      "e_in_hopMembers": {
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "hopMembers",
          "port": "collection"
        }
      },
      "e_in_hopHubs": {
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "hopHubs",
          "port": "collection"
        }
      },
      "e_in_exceptMembers": {
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "exceptMembers",
          "port": "collection"
        }
      },
      "e_excl_members": {
        "from": {
          "node": "hopMembers",
          "port": "collection"
        },
        "to": {
          "node": "exceptMembers",
          "port": "exclude"
        }
      },
      "e_keep_exceptHubs": {
        "from": {
          "node": "exceptMembers",
          "port": "collection"
        },
        "to": {
          "node": "exceptHubs",
          "port": "collection"
        }
      },
      "e_excl_hubs": {
        "from": {
          "node": "hopHubs",
          "port": "collection"
        },
        "to": {
          "node": "exceptHubs",
          "port": "exclude"
        }
      },
      "e_colHome_eq": {
        "from": {
          "node": "colHome",
          "port": "value"
        },
        "to": {
          "node": "eqHome",
          "port": "left"
        }
      },
      "e_litHome_eq": {
        "from": {
          "node": "litHome",
          "port": "value"
        },
        "to": {
          "node": "eqHome",
          "port": "right"
        }
      },
      "e_in_filterHome": {
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "filterHome",
          "port": "collection"
        }
      },
      "e_eqHome_filter": {
        "from": {
          "node": "eqHome",
          "port": "value"
        },
        "to": {
          "node": "filterHome",
          "port": "predicate"
        }
      },
      "e_keep_exceptHome": {
        "from": {
          "node": "exceptHubs",
          "port": "collection"
        },
        "to": {
          "node": "exceptHome",
          "port": "collection"
        }
      },
      "e_excl_home": {
        "from": {
          "node": "filterHome",
          "port": "collection"
        },
        "to": {
          "node": "exceptHome",
          "port": "exclude"
        }
      },
      "e_colArchive_eq": {
        "from": {
          "node": "colArchive",
          "port": "value"
        },
        "to": {
          "node": "eqArchive",
          "port": "left"
        }
      },
      "e_litArchive_eq": {
        "from": {
          "node": "litArchive",
          "port": "value"
        },
        "to": {
          "node": "eqArchive",
          "port": "right"
        }
      },
      "e_in_filterArchive": {
        "from": {
          "node": "corpus",
          "port": "collection"
        },
        "to": {
          "node": "filterArchive",
          "port": "collection"
        }
      },
      "e_eqArchive_filter": {
        "from": {
          "node": "eqArchive",
          "port": "value"
        },
        "to": {
          "node": "filterArchive",
          "port": "predicate"
        }
      },
      "e_keep_exceptArchive": {
        "from": {
          "node": "exceptHome",
          "port": "collection"
        },
        "to": {
          "node": "exceptArchive",
          "port": "collection"
        }
      },
      "e_excl_archive": {
        "from": {
          "node": "filterArchive",
          "port": "collection"
        },
        "to": {
          "node": "exceptArchive",
          "port": "exclude"
        }
      },
      "e_sort": {
        "from": {
          "node": "exceptArchive",
          "port": "collection"
        },
        "to": {
          "node": "sort",
          "port": "collection"
        }
      },
      "e_project": {
        "from": {
          "node": "sort",
          "port": "collection"
        },
        "to": {
          "node": "project",
          "port": "collection"
        }
      },
      "e_out": {
        "from": {
          "node": "project",
          "port": "collection"
        },
        "to": {
          "node": "out",
          "port": "value"
        }
      }
    }
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
