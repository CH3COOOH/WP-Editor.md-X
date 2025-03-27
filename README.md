# WP-Editor.md-X

## What's this?
Copy of the project [WP-Editor.md](https://github.com/LuRenJiasWorld/WP-Editor.md), which was "the best WordPress Markdown editor" (maybe that's true) but has stopped updating for years with lots of issues remaining. One of the most serious issue is that, the editor would **pull JS files from remote CDNs** (https://cdn.jsdelivr.net) instead of the local WP resources, while **recently the CDNs were died in some area (403 error)** and the editor has been unavailable.  

In fact, I noticed that **the plugin contains all JS files it needs** in directory `/assets`, so it is hard for me to understand why it was designed to pull JS files remotely. After my professional treatment, you will see the plugin can launch the MarkDown editor without pulling any remote resources.  

I deeply love this plugin, thus I know **it is my duty to MAKE WP-Editor.md GREAT AGAIN**.  

**The world needs hero, and that is what I will be**.

## What changed

* In `/src/Admin/Controller.php`:

```php
// $this->front_static_url = Config::get_option("editor_addres", "editor_style");
$this->front_static_url = "/wp-content/plugins/wp-editormd";
```

* In `/assets/Editormd/editormd.min.js`

```php
// x.mermaidURL={js:"//cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min"}
x.mermaidURL={js:"/wp-content/plugins/wp-editormd/assets/Mermaid/mermaid.min"}
```