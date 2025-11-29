# dev-cheatsheet-content

This repository stores all cheat sheet content used by the
**dev-cheatsheet** web application.
Each cheat sheet is written in **Markdown**, kept clean, structured, and
easy to update.

The goal is to keep content fully decoupled from the UI so that notes
can evolve independently of the frontend code.

------------------------------------------------------------------------

## 📁 Structure

Cheat sheets are organized by topic:

    /linux
    /sql
    /git
    /networking
    /javascript
    ...

Each folder contains `.md` files such as:

    linux/
      basics.md
    sql/
      queries.md
      joins.md
    git/
      commands.md

This structure keeps everything modular and simple to maintain.

------------------------------------------------------------------------

## 📄 Cheat Sheet Index (JSON)

To make it easy for the **dev-cheatsheet web app** to list and organize
all available files, this repository includes a central JSON file that
defines:

-   All categories
-   The files inside each category
-   The paths to the markdown or HTML cheat sheets (**at the momemnt html files not supported**)
-   The display names used in the UI

The JSON file serves as the **single source of truth** for the frontend.

This approach makes it simple to:

-   Add new cheat sheets without editing frontend code
-   Control sorting, naming, and grouping
-   Keep UI and content fully independent
-   Reduce filesystem scanning complexity

------------------------------------------------------------------------

## 📁 JSON Structure

``` json
{
  "title": "dev-cheatsheet",
  "description": "This is the default cheatsheet source.",
  "category": [
    {
      "name": "Linux",
      "files": [
        {
          "name": "Simple Commands",
          "path": "/linux/basics.md"
        }
      ]
    },
    {
      "name": "SQL",
      "files": [
        {
          "name": "Queries",
          "path": "/sql/queries.md"
        },
        {
          "name": "joins",
          "path": "/sql/joins.md"
        }
      ]
    }
  ]
}
```

------------------------------------------------------------------------

## 🧩 How It Works

-   **`category`**: Defines the main sections (Linux, SQL, Windows,
    etc.).
-   **`files`**: Contains the cheat sheets inside each category.
-   **`name`**: Display name shown in the web UI.
-   **`path`**: Relative path to the markdown/HTML file inside this
    repository.

The web app reads this JSON at startup and builds the UI automatically.

------------------------------------------------------------------------

## 🔧 Updating the Index

Whenever you add a new cheat sheet:

1.  Place the `.md` or `.html` file in the correct folder. (**at the momemnt html files not supported**)
2.  Add a matching entry inside the JSON file.
3.  The dev-cheatsheet web app will display it automatically.

No additional configuration or frontend modifications are required.

------------------------------------------------------------------------

## 🔮 Future Possibilities

-   Metadata (title, tags, language)
-   Auto-generation of the JSON file

------------------------------------------------------------------------

## 📜 License

This content is licensed under the MIT License.
