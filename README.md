# Sinatra Web Server
## Repo details
| Details   |  | 
| :--------------- | -------: |
| Re-created by: | The Recode Team |
| Version:    | 0.0.1   |
## Purpose  
As an transitional educational tool before the magic of Rails, this framework was built using Sinatra and modelled after Rails' file structure. It utilizes Sinatra's extension of ActiveRecord. Unlike Rails, it is fully flexible and less opinionated.
<br>
## Supports
1. Local Support
2. Heroku Support (Disabled for now)

>**NOTE**:
>This guide assumes you are good with Ruby and understand MVC architecture patterns.

## Common Setup
1) Clone the repo to your local machine.

2) Rename the skeleton if needed.
```
$ mv sinatra-web-server <your-desired-app-name>
```
3) Run bundle install.
```
$ cd <your-desired-app-name>
$ bundle install  
# Open issue in this github repo if any issue
```
4) Perform a short test by launching the server.
```
$ shotgun config.ru
```
5) Hooray! You may now begin your code development.

### To Include/Remove a Gem
1) Include/remove your gem inside Gemfile depending on group. Please note that Heroku will use production only.
```
# File location: <repo_root>\Gemfile
```
2) Perform bundle install
```
$ bundle install
```
3) Head to **config\environments\init.rb** to ensure your require is aligned to your adjustment.
```
# Perform requiring gem that we need
#######################################################
	# basic
require 'rubygems'
require 'bundler/setup' if File.exists?(ENV['BUNDLE_GEMFILE'])
require 'pathname'

	# database
require 'pg'
require 'active_record'
require 'logger'

	# sinatra
require 'sinatra'
require "sinatra/reloader" if development?

	# embedded ruby
require 'erb'
require 'uri'

	# Additional Gem includes after this comments
#######################################################
```
4) Done. You're ready. 

## To Create Controllers
You can create a controller ruby file inside **app/controllers** manually. As long as there is no conflicted routes, you can create many controller files. Sinatra will go through each controller file and compile all available routes.

In this example, let's create 'sessions' routing:
```
# app/controllers/users.rb

get '/signup' do
	erb :'users/new'
end

post '/signup' do
	# Do something processing with user input
	redirect to '/user/dashboard'
end

get '/user/dashboard' do
	erb :dashboard
end
```

## To Create Views  

You can create a view erb file inside **app/views** manually. This framework uses erb gem to generate the view. Views can be created in full-form or partial-form. Examples,  

#### To create simple erb view file:
```
# app/views/root.erb
<h1>This is root page</h1>  

# To route it, use ' erb :root ' in controller
```
#### To create erb view file inside a sub-folder:
```
# app/views/users/new.erb
<h1>This is signup page</h1>
...
# To route it, use ' erb :"users/new" ' in controller
```
#### To create partial erb view file:
```
# app/views/partials/form.erb
<h1>This is partial forms for AJAX calls</h1>
...


# To use it in existing view .erb file, example:
	# in app/views/users/new.erb
	<h2> User Data </h2>
	<%= erb :"partial/form" %>
```

## To Create Helpers
Helper files can be created inside **app/helpers** manually. Example:
```
# app/helpers/html.rb
helpers do
	# for repetitive <em> in html view
	def em(param)
		...
	end

	# for repetitive math calculation
	def calculate_square(param)
		param * param
	end
	
	# More repetitive functions
	...
end
```
<br>  

Any function within helpers loop can be called directly similar to a Ruby method. Example:  

```
# app/controllers/root.rb
post '/' do
	calculate_square(params[:input])
end

# app/views/root.erb
<html>
	<br>
	<%= em("String") %>
	<br>
</html>
```
More information can be found here: http://www.sinatrarb.com/faq.html#helpview
<br>
