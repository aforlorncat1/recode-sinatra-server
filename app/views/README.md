app/views
=================
This is view folder which holds your html outputs. You have the freedom to create any file or sub-folders.


<br>
#### To create a simple erb view:
```
# app/views/root.erb
<h1>This is root page</h1>
...
# To route it, use ' erb :root ' in the corresponding controller.
```
<br>
#### To create an erb view inside a sub-folder:
```
# app/views/users/new.erb
<h1>This is signup page</h1>
...
# To route it, use ' erb :"users/new" ' in the corresponding controller.
```

<br>
#### To create partial erb views:
```
# app/views/partials/form.erb
<h1>This is a partial form for AJAX calls</h1>
...
# To use it in an existing view .erb file:
	# in app/views/users/new.erb
	<h2> User Data </h2>
	<%= erb :"partial/form" %>
```
