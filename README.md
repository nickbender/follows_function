#Follows Function

_Form follows function_ is a principle associated with modern architecture and industrial design in the 20th century. The principle is that the shape of a building or object should be primarily based upon its intended function or purpose. 

The __Follows Function__ gem seeks to make your rails form code work even more magically and cleanly than the rails defaults.  It allows clean syntax, easy integration with a number of different css frameworks, and implements fun features like client side validation and searchable multi-select (via jquery.Chosen).

So to begin...

```ruby
  gem 'follows_function'
```

Should be in your Gemfile.  And as usual..

```
  $ bundle install
```

There are a number of helpful generator functions to prep follows_function for your app.

```
  $ rails generate ff:bootstrap
  $ rails generate ff:pure
  $ rails generate ff:neat
  ...
  # etc
```

Each generator adds requisite css and js to your _application_ files, as well as establishes defaults for client-side-validation display. There are a number of configurable SASS variables for each framework that can be configured to your given tastes. They can be found [here](#).

Syntax for your forms will remain largely the same as they currently do, but can be further customized.

```
  <%= form_ff_for(@object, 
                ff: { validate: true, 
                chosen_select: true,
                labels: expand,
                input_width: 'span3'
              }) do |f|
    <%= f.input
    # etc
    end
    %>
```

As you can see, the :ff hash contains many options that can be passed to individual forms, or also set as defaults in a config file:

```
FollowsFunction.configure do |config|
  config.validate = true
  config.chosen_select = true
  config.css = bootstrap
  #...
  #etc
end
```

##Why?
At Margin, we found ourselves using a lot of the same gems in every project.  Simpleform, ClientSideValidations, Chosen, and various css frameworks, but realized the task of inserting all these into a new app was both tedius and time consuming given the vast number of pieces in motion.

##Where's My Framework?
If you find that we're missing your favorite open source css library, you can see our guide on integrating your own variables and helpers [here](#).

##Won't this cause a lot of bloat?
FollowsFunction dynamically inserts only the framework assets you need both into your app and onto your slug. The approriate css and javascript assets are only included if you specify them in a config file or use them on a form.  Plus, the gem's total size is only X.

##What if I want to use a jquery plugin that's not included?
Feel free to send us a PR including any library you think is crucial that we've missed. See our [guide](#) on how to do so. Be warned though, we have some strong opinions, and won't increase our footprint unless we feel it adds to the gem's overall functionality.

##License
[MIT](http://www.tldrlegal.com/license/mit-license) - Go nuts!

