---
layout: post
title:      "Rails as an API"
date:       2020-08-17 20:46:29 +0000
permalink:  rails_as_an_api
---


There are so many fun surprises that come with Rails and one particularly interesting is its ability to be an Application Programming Interface (API). Rails can act as both the frontend and backend of a website, but it can also serve as an API. Let's review: an API helps one system communicate with another external system. APIs are data repositories that slim down logic and are easier to work with. Using Rails, we can create our own APIs and share our information on the web. When building frontend applications using JavaScript or handling asynchronous requests our Rails API can render JSON strings, making our application build a breeze. Let's take a closer look. 

To build an API-only Rails application, use --api after the Rails application name like so:

```
rails new cookie-cruncher-api --api
```

The --api flag tells Rails to not generate views, have controllers inherit from ActionController::API instead of ActionController::Base and remove certain default features and middleware that won't be needed.

Don't forget we can use generators to help us set up our migrations, models, and controllers.

```
rails g resource cookie type ingredients
```

Add actions to your controllers:

```
def index
  cookies = Cookie.all
  render json: cookies, include: [:type, :ingredients]
end
```

To test your APIs while developing them locally, you'll need to understand Cross-Origin Resource Sharing, also known as CORS. CORS allows browsers to give an application running at one origin, access to resources from a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin other than its own. CORS adds security measures that restrict scripts like fetch() from accessing a resource from an origin that is not on the invite list. 

Make sure your Gemfile has rack-cors included:

```
 gem 'rack-cors'
```

Then, add the following to config/application.rb inside class Application < Rails::Application:

```
 config.middleware.insert_before 0, Rack::Cors do
      allow do
        origins '*'
        resource '*',
          :headers => :any,
          :methods => [:get, :post, :delete, :put, :patch, :options, :head],
          :max_age => 0
      end
    end
```

You can now start up your API and begin sending requests to it.

