app/controllers/*.rb
=================
This is your routing and logic folder. Basic routing requires a url address and a destination.
This framework provides full flexibility and room for
customization.

For example, a users controller file might look something like this:
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
Remember to link/require the appropriate controller if you require access to their related objects.

You can create many controller files as long as there is no conflicted routes. Sinatra go through
each controller file and compile all available routes.