# Fixing ExecJS errors on Windows

If you're running your Rails application on your Windows machine, and experiencing this issue:

```
ExecJS::RuntimeError
```

Here's the solution. 

In your project's ```app/assets/javascripts/application.js``` file, remove the last two lines that read:

```
//= require turbolinks
//= require_tree .
```