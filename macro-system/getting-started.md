# Getting Started

Let's put together a simple system to CRUD "macros". Macros are bits of text stored in the database and called by a name. For instance sending a message with `++docker` would display a link and message regarding docker.

We'll implement the following commands:

* Create/Update Macro: `++add name=docker,message=Check out https://docker.io!`
* Delete Macro `++delete name=docker`
* List all Macros: `++list`

