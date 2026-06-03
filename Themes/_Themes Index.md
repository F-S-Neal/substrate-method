# Themes Index

Every theme tag you've created (namespaced `#theme/...`) and how many sparks carry it.
Pick one that's accrued enough material and make its page from the Theme template.

```dataview
TABLE length(rows) AS sparks
FROM "Sparks"
FLATTEN file.tags AS tag
WHERE startswith(tag, "#theme/")
GROUP BY tag
SORT length(rows) DESC
```

(The Tag pane in Obsidian's right sidebar also groups all your themes under "theme".)
