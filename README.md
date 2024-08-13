# aps-da4acad-dgn2dwg2pdf

## This is a work in progress

## DGN TO DWG
Activity below:
```json
{
	"id": "Your activity name",
	"commandLine": [
		"$(engine.path)\\accoreconsole.exe /s $(settings[script].path)"
	],
	"parameters": {
		"inputdgn": {
			"verb": "get",
			"description": "input DGN file",
			"required": true,
			"localName": "input.dgn"
		},
		"result": {
			"verb": "put",
			"description": "resultdrawing",
			"required": true,
			"localName": "result.dwg"
		}
	},
	"engine": "Autodesk.AutoCAD+25_0",
	"description": "DGNtoDWG",
	"settings": {
		"script": "(command\"-dgnimport\" \"input.dgn\" \"\" \"\" \"\" \"save\" \"result.dwg\")\n"
	}
}
```
You must use the engine Autodesk.AutoCAD+25_0

Workitem below:

```json
{
  "activityId": "Your activity fully qualified id",
  "arguments": {
    "inputdgn": {
      "url": "urn:adsk.objects:os.object:<<bucketkey>>/somedgnfile.dgn",
      "verb": "get",
      "Headers": {
        "Authorization": "Bearer yourtokenhere"
      }
    },
    "result": {
      "verb": "put",
      "url": "urn:adsk.objects:os.object:<<bucketkey>>/somedgnfile.dwg",
      "Headers": {
        "Authorization": "Bearer yourtokenhere"
      }
    },
    "onProgress": {
      "verb": "post",
      "url": "yourcallbackurl",
      "Headers": {
        "Content-Type": "application/json"
      }
    },
    "onComplete": {
      "verb": "post",
      "url": "yourcallbackurl",
      "Headers": {
        "Content-Type": "application/json"
      }
    }
  }
}
```

## DWG to PDF 

Simply use the shared activity `AutoCAD.PlotToPDF+prod`

Workitem below:
```json
{
  "activityId": "AutoCAD.PlotToPDF+prod",
  "arguments": {
    "HostDwg": {
      "url": "urn:adsk.objects:os.object:<<bucketkey>>/somedgnfile.dwg",
      "verb": "get",
      "Headers": {
        "Authorization": "Bearer yourtokenhere"
      }
    },
    "Result": {
      "verb": "put",
      "url": "urn:adsk.objects:os.object:<<bucketkey>>/somedgnfile.pdf",
      "Headers": {
        "Authorization": "Bearer yourtokenhere"
      }
    },
    "onProgress": {
      "verb": "post",
      "url": "yourcallbackurl",
      "Headers": {
        "Content-Type": "application/json"
      }
    },
    "onComplete": {
      "verb": "post",
      "url": "yourcallbackurl",
      "Headers": {
        "Content-Type": "application/json"
      }
    }
  }
}
```
