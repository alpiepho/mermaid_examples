# kdic_diagrams

Several months ago I stumbled on a new feature that was added to GitHub Markdown, “mermaid.js”.  This is a JavaScript library that uses the d3.js library for data visibility.  Really cool stuff.  

Here are links to the library:

https://github.com/mermaid-js/mermaid/blob/develop/README.md

https://github.com/mermaid-js/mermaid/blob/develop/docs/developer-docs/configuration.md

https://github.com/mermaid-js/mermaid/blob/develop/docs/usage.md


## Simple Examples

```mermaid
sequenceDiagram
    participant dotcom
    participant iframe
    participant viewscreen
    dotcom->>iframe: loads html w/ iframe url
    iframe->>viewscreen: request template
    viewscreen->>iframe: html & javascript
    iframe->>dotcom: iframe ready
    dotcom->>iframe: set mermaid data on iframe
    iframe->>iframe: render mermaid
```


```mermaid
classDiagram
    title Animal Diagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
	+String beakColor
	+swim()
	+quack()
    }
    class Fish{
	-int sizeInFeet
	-canEat()
    }
    class Zebra{
	+bool is_wild
	+run()
    }
```

## OPTIONS TO RUN LOCALLY - PYTHON

```
python3 -m http.server 8000
```

Then access with http://localhost:8000


## OPTIONS TO RUN LOCALLY - GOLANG

Create file server.go where mermaid html files are: 

```
package main

import (
	"log"
	"net/http"
)

func main() {
	fs := http.FileServer(http.Dir("./static"))
	http.Handle("/", fs)

	log.Print("Listening on :3000...")
	err := http.ListenAndServe(":3000", nil)
	if err != nil {
		log.Fatal(err)
	}
}

```

## OPTIONS TO RUN LOCALLY - VS CODE LIVESERVER

The VS Code Plugin "Live Server" by Ritwick Dey works to view mermaid pages.  Install and then use the command pallette to open a file.


## REFERENCES

https://jojozhuang.github.io/tutorial/mermaid-cheat-sheet/

