# API Integration Repository

For integrating apis into bigquery using cloud build and composer managed by terraform

The current set up builds correctly, now am trying to ensure the second step pulls this repo. 

`name unknown: Repository "bytecode-p-tera-api-dev-repo" not found` is the current bug showing up in the second step of the build. Not sure whats up with this particularly, but it might be because the full-string isn't resolved to the repo url. TBD