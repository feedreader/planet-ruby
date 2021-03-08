# Day 4 - glimmer-dsl-opal Gem  - Script Web Widgets with Two-Way Data-Binding - Ruby <3 JavaScript - Thanks to Opal, the Ruby to JavaScript Source-to-Source Compiler


Written by {% avatar AndyObtiva %} [Andy Maleh](https://github.com/AndyObtiva)

_Software Engineering Expert from Montreal, Quebec. Creator of [Glimmer](https://github.com/AndyObtiva/glimmer) and [Abstract Feature Branch](https://github.com/AndyObtiva/abstract_feature_branch). Speaker at RailsConf, RubyConf, AgileConf, EclipseCon, EclipseWorld. Master in Software Engineering, DePaul University, Chicago. Blogs at [Code Mastery Takes Commitment To Bold Coding Adventures](http://andymaleh.blogspot.com/). Snowboarder and Drummer._



## What's Glimmer for Opal on Rails?

[Glimmer for Opal](https://github.com/AndyObtiva/glimmer-dsl-opal) is a gem that enables building web apps in ruby via [Opal](https://opalrb.com/) running on rails.

Use in one of two ways:
- **Direct:** build the graphical user interface of web apps with the same friendly scripting language syntax as Glimmer for the Standard Widget Toolkit (SWT), thus requiring a lot less code
and avoiding opaque web concepts like 'render' and 'reactive'. No HTML/JS/CSS skills are even required. Web designers may be involved with CSS styling only if needed.
- **Adapter:** auto-webify Glimmer desktop apps (i.e. apps built with Glimmer
for the Standard Widget Toolkit (SWT) via Opal running on Rails without changing a line of code. Just insert them as a single require statement in a rails app, and boom! They're running on the web! Apps may then optionally be custom-styled for the web by web designers with standard CSS if needed.

Glimmer for Opal successfully reuses the entire Glimmer core domain-specific language engine in Opal inside a web browser, and as such inherits the full range of powerful Glimmer desktop two-way data-binding capabilities for the web.


## Principles

- **Live in Rubyland via the Glimmer scripting language**, completely oblivious to web browser technologies.
- **HTML is for creating documents not interactive applications**. As such, software engineers can avoid it and focus on creating web applications more productively with Glimmer for Opal in ruby instead (just like they do in desktop development) while content creators and web designers can be the ones responsible for creating HTML documents for web content purposes only as HTML was originally intended. That way, Glimmer web user interfaces are used and embedded in web pages when providing users with applications while the rest of the web pages are maintained by non-engineers as HTML. This achieves a correct separation of responsibilities and better productivity and maintainability.
- **Approximate styles by developers via the Glimmer scripting language. Perfect styles by designers via pure CSS**. Developers can simply build user interfaces with approximate styling similar to the desktop and mockups without worrying about pixel-perfect aesthetics. Web designers can take styling further with CSS since every HTML element auto-generated by Glimmer for Opal
has a predictable ID and CSS class. This achieves a proper separation of responsibilities between developers and designers.
- **Web servers are used just like servers in traditional client/server architecture**, meaning they simply provide remote method invocation (RMI) services to enable centralizing some of the application logic and data in the cloud to make available everywhere and enable data-sharing with others.
- **Forget Routers!** Glimmer for Opal supports auto-routing of custom shells (windows), which are opened as separate tabs in a web browser with automatically generated routes and bookmarkable web pages.


## Live Development

Glimmer for Opal is a new project in live development and is undergoing many changes due to its highly unusual and imaginative nature. As such, I am currently welcoming of feedback and ideas for the project, the more radical and innovative the better. It is time to upend the inferior javascript framework era as we know it!


## Getting Started Samples

Glimmer for Opal comes with [many samples](https://github.com/AndyObtiva/glimmer-dsl-opal#samples), including:


#### Hello, World!

```ruby
include Glimmer

shell {
  text 'Glimmer'
  label {
    text 'Hello, World!'
  }
}.open
```

![](i/glimmer-dsl-opal-hello-world.png)



#### Hello, Table!

```ruby
class HelloTable
  class BaseballGame
    class << self
      attr_accessor :selected_game

      def all_playoff_games
        @all_playoff_games ||= {
          'NLDS' => [
            new(Time.new(2037, 10, 6, 12, 0),  'Chicago Cubs', 'Milwaukee Brewers', 'Free Bobblehead'),
            new(Time.new(2037, 10, 7, 12, 0),  'Chicago Cubs', 'Milwaukee Brewers'),
            new(Time.new(2037, 10, 8, 12, 0),  'Milwaukee Brewers', 'Chicago Cubs'),
            new(Time.new(2037, 10, 9, 12, 0),  'Milwaukee Brewers', 'Chicago Cubs'),
            new(Time.new(2037, 10, 10, 12, 0), 'Milwaukee Brewers', 'Chicago Cubs', 'Free Umbrella'),
            new(Time.new(2037, 10, 6, 18, 0),  'Cincinnati Reds', 'St Louis Cardinals', 'Free Bobblehead'),
            new(Time.new(2037, 10, 7, 18, 0),  'Cincinnati Reds', 'St Louis Cardinals'),
            new(Time.new(2037, 10, 8, 18, 0),  'St Louis Cardinals', 'Cincinnati Reds'),
            new(Time.new(2037, 10, 9, 18, 0),  'St Louis Cardinals', 'Cincinnati Reds'),
            new(Time.new(2037, 10, 10, 18, 0), 'St Louis Cardinals', 'Cincinnati Reds', 'Free Umbrella'),
          ],
          'ALDS' => [
            new(Time.new(2037, 10, 6, 12, 0),  'New York Yankees', 'Boston Red Sox', 'Free Bobblehead'),
            new(Time.new(2037, 10, 7, 12, 0),  'New York Yankees', 'Boston Red Sox'),
            new(Time.new(2037, 10, 8, 12, 0),  'Boston Red Sox', 'New York Yankees'),
            new(Time.new(2037, 10, 9, 12, 0),  'Boston Red Sox', 'New York Yankees'),
            new(Time.new(2037, 10, 10, 12, 0), 'Boston Red Sox', 'New York Yankees', 'Free Umbrella'),
            new(Time.new(2037, 10, 6, 18, 0),  'Houston Astros', 'Cleveland Indians', 'Free Bobblehead'),
            new(Time.new(2037, 10, 7, 18, 0),  'Houston Astros', 'Cleveland Indians'),
            new(Time.new(2037, 10, 8, 18, 0),  'Cleveland Indians', 'Houston Astros'),
            new(Time.new(2037, 10, 9, 18, 0),  'Cleveland Indians', 'Houston Astros'),
            new(Time.new(2037, 10, 10, 18, 0), 'Cleveland Indians', 'Houston Astros', 'Free Umbrella'),
          ],
          'NLCS' => [
            new(Time.new(2037, 10, 12, 12, 0), 'Chicago Cubs', 'Cincinnati Reds', 'Free Towel'),
            new(Time.new(2037, 10, 13, 12, 0), 'Chicago Cubs', 'Cincinnati Reds'),
            new(Time.new(2037, 10, 14, 12, 0), 'Cincinnati Reds', 'Chicago Cubs'),
            new(Time.new(2037, 10, 15, 18, 0), 'Cincinnati Reds', 'Chicago Cubs'),
            new(Time.new(2037, 10, 16, 18, 0), 'Cincinnati Reds', 'Chicago Cubs'),
            new(Time.new(2037, 10, 17, 18, 0), 'Chicago Cubs', 'Cincinnati Reds'),
            new(Time.new(2037, 10, 18, 12, 0), 'Chicago Cubs', 'Cincinnati Reds', 'Free Poncho'),
          ],
          'ALCS' => [
            new(Time.new(2037, 10, 12, 12, 0), 'Houston Astros', 'Boston Red Sox', 'Free Towel'),
            new(Time.new(2037, 10, 13, 12, 0), 'Houston Astros', 'Boston Red Sox'),
            new(Time.new(2037, 10, 14, 12, 0), 'Boston Red Sox', 'Houston Astros'),
            new(Time.new(2037, 10, 15, 18, 0), 'Boston Red Sox', 'Houston Astros'),
            new(Time.new(2037, 10, 16, 18, 0), 'Boston Red Sox', 'Houston Astros'),
            new(Time.new(2037, 10, 17, 18, 0), 'Houston Astros', 'Boston Red Sox'),
            new(Time.new(2037, 10, 18, 12, 0), 'Houston Astros', 'Boston Red Sox', 'Free Poncho'),
          ],
          'World Series' => [
            new(Time.new(2037, 10, 20, 18, 0), 'Chicago Cubs', 'Boston Red Sox', 'Free Baseball Cap'),
            new(Time.new(2037, 10, 21, 18, 0), 'Chicago Cubs', 'Boston Red Sox'),
            new(Time.new(2037, 10, 22, 18, 0), 'Boston Red Sox', 'Chicago Cubs'),
            new(Time.new(2037, 10, 23, 18, 0), 'Boston Red Sox', 'Chicago Cubs'),
            new(Time.new(2037, 10, 24, 18, 0), 'Boston Red Sox', 'Chicago Cubs'),
            new(Time.new(2037, 10, 25, 18, 0), 'Chicago Cubs', 'Boston Red Sox'),
            new(Time.new(2037, 10, 26, 18, 0), 'Chicago Cubs', 'Boston Red Sox', 'Free World Series Polo'),
          ]
        }
      end

      def playoff_type
        @playoff_type ||= 'World Series'
      end

      def playoff_type=(new_playoff_type)
        @playoff_type = new_playoff_type
        self.schedule=(all_playoff_games[@playoff_type])
      end

      def playoff_type_options
        all_playoff_games.keys
      end

      def schedule
        @schedule ||= all_playoff_games[playoff_type]
      end

      def schedule=(new_schedule)
        @schedule = new_schedule
      end
    end

    include Glimmer
    include Glimmer::DataBinding::ObservableModel

    TEAM_BALLPARKS = {
      'Boston Red Sox'     => 'Fenway Park',
      'Chicago Cubs'       => 'Wrigley Field',
      'Cincinnati Reds'    => 'Great American Ball Park',
      'Cleveland Indians'  => 'Progressive Field',
      'Houston Astros'     => 'Minute Maid Park',
      'Milwaukee Brewers'  => 'Miller Park',
      'New York Yankees'   => 'Yankee Stadium',
      'St Louis Cardinals' => 'Busch Stadium',
    }

    attr_accessor :date_time, :home_team, :away_team, :ballpark, :promotion

    def initialize(date_time, home_team, away_team, promotion = 'N/A')
      self.date_time = date_time
      self.home_team = home_team
      self.away_team = away_team
      self.promotion = promotion
      observe(self, :date_time) do |new_value|
        notify_observers(:game_date)
        notify_observers(:game_time)
      end
    end

    def home_team=(home_team_value)
      if home_team_value != away_team
        @home_team = home_team_value
        self.ballpark = TEAM_BALLPARKS[@home_team]
      end
    end

    def away_team=(away_team_value)
      if away_team_value != home_team
        @away_team = away_team_value
      end
    end

    def date
      Date.new(date_time.year, date_time.month, date_time.day)
    end

    def time
      Time.new(0, 1, 1, date_time.hour, date_time.min, date_time.sec, '+00:00')
    end

    def game_date
      date_time.strftime("%m/%d/%Y")
    end

    def game_time
      date_time.strftime("%I:%M %p")
    end

    def home_team_options
      TEAM_BALLPARKS.keys
    end

    def away_team_options
      TEAM_BALLPARKS.keys
    end

    def ballpark_options
      [TEAM_BALLPARKS[@home_team], TEAM_BALLPARKS[@away_team]]
    end

    def to_s
      "#{home_team} vs #{away_team} at #{ballpark} on #{game_date} #{game_time}"
    end

    def book!
      "Thank you for booking #{to_s}"
    end
  end

  include Glimmer

  def launch
    shell {
      grid_layout

      text 'Hello, Table!'

      label {
        layout_data :center, :center, true, false

        text 'Baseball Playoff Schedule'
        font height: 30, style: :bold
      }

      combo(:read_only) {
        layout_data :center, :center, true, false
        selection bind(BaseballGame, :playoff_type)
        font height: 16
      }

      table(:editable) { |table_proxy|
        layout_data :fill, :fill, true, true

        table_column {
          text 'Game Date'
          width 150
          sort_property :date # ensure sorting by real date value (not `game_date` string specified in items below)
          editor :date_drop_down, property: :date_time
        }
        table_column {
          text 'Game Time'
          width 150
          sort_property :time # ensure sorting by real time value (not `game_time` string specified in items below)
          editor :time, property: :date_time
        }
        table_column {
          text 'Ballpark'
          width 180
          editor :none
        }
        table_column {
          text 'Home Team'
          width 150
          editor :combo, :read_only # read_only is simply an SWT style passed to combo widget
        }
        table_column {
          text 'Away Team'
          width 150
          editor :combo, :read_only # read_only is simply an SWT style passed to combo widget
        }
        table_column {
          text 'Promotion'
          width 150
          # default text editor is used here
        }

        # Data-bind table items (rows) to a model collection property, specifying column properties ordering per nested model
        items bind(BaseballGame, :schedule), column_properties(:game_date, :game_time, :ballpark, :home_team, :away_team, :promotion)

        # Data-bind table selection
        selection bind(BaseballGame, :selected_game)

        # Default initial sort property
        sort_property :date

        # Sort by these additional properties after handling sort by the column the user clicked
        additional_sort_properties :date, :time, :home_team, :away_team, :ballpark, :promotion
      }

      button {
        text 'Book Selected Game'
        layout_data :center, :center, true, false
        font height: 16
        enabled bind(BaseballGame, :selected_game)

        on_widget_selected {
          book_selected_game
        }
      }
    }.open
  end

  def book_selected_game
    message_box {
      text 'Baseball Game Booked!'
      message BaseballGame.selected_game.book!
    }.open
  end
end

HelloTable.new.launch
```

![](i/glimmer-dsl-opal-hello-table.png)

Hello, Table! Editing Game Date

![](i/glimmer-dsl-opal-hello-table-editing-game-date.png)





## Auto-Webify Demos

### Glimmer Calculator

[Glimmer Calculator](https://github.com/AndyObtiva/glimmer-cs-calculator) is a Glimmer project that runs on both the web and desktop with the same exact Glimmer code (which was generated originally via [Glimmer Scaffolding](https://github.com/AndyObtiva/glimmer-dsl-swt#scaffolding))!


```ruby
require 'easily_typable'

require 'models/glimmer/calculator/presenter'

module Glimmer
  class Calculator
    include Glimmer::UI::CustomShell

    APP_ROOT = File.expand_path('../../../..', __FILE__)
    VERSION = File.read(File.expand_path(File.join('..', '..', '..', '..', 'VERSION'), __FILE__))
    LICENSE = File.read(File.expand_path(File.join('..', '..', '..', '..', 'LICENSE.txt'), __FILE__))

    ## Add options like the following to configure CustomShell by outside consumers
    #
    # options :title, :background_color
    # option :width, 320
    # option :height, 240

    ## Uncomment before_body block to pre-initialize variables to use in body
    #
    #
    before_body {
      @presenter = Presenter.new
      @button_font = {height: 14}
      @button_font_operation = {height: 18}
      @button_font_big = {height: 28}
      Display.setAppName('Glimmer Calculator')
      @display = display {
        on_about {
          display_about_dialog
        }
        on_preferences {
        # No need for preferences. Just display about dialog.
          display_about_dialog
        }
        on_swt_keydown { |key_event|
          char = key_event.character.chr rescue nil
          @presenter.press(char)
        }
      }
    }

    ## Uncomment after_body block to setup observers for widgets in body
    #
    # after_body {
    #
    # }

    ## Add widget content inside custom shell body
    ## Top-most widget must be a shell or another custom shell
    #
    body {
      shell {
        minimum_size (OS.mac? ? 320 : (OS.windows? ? 390 : 520)), 240
        image File.join(APP_ROOT, 'package', 'windows', "Glimmer Calculator.ico") if OS.windows?
        text "Glimmer - Calculator"
        grid_layout 4, true
        # Setting styled_text to multi in order for alignment options to activate
        styled_text(:multi, :wrap, :border) {
          text bind(@presenter, :result)
          alignment swt(:right)
          right_margin 5
          font height: 40
          layout_data(:fill, :fill, true, true) {
            horizontal_span 4
          }
          editable false
          caret nil
        }
        command_button('AC')
        operation_button('÷')
        operation_button('×')
        operation_button('−')
        (7..9).each { |number|
          number_button(number)
        }
        operation_button('+', font: @button_font_big, vertical_span: 2)
        (4..6).each { |number|
          number_button(number)
        }
        (1..3).each { |number|
          number_button(number)
        }
        command_button('=', font: @button_font_big, vertical_span: 2)
        number_button(0, horizontal_span: 2)
        operation_button('.')
      }
    }

    def number_button(number, options = {})
      command_button(number, options)
    end

    def operation_button(operation, options = {})
      command_button(operation, options.merge(font: @button_font_operation))
    end

    def command_button(command, options = {})
      command = command.to_s
      options[:font] ||= @button_font
      options[:horizontal_span] ||= 1
      options[:vertical_span] ||= 1

      button { |proxy|
        text command
        font options[:font]

        layout_data(:fill, :fill, true, true) {
          horizontal_span options[:horizontal_span]
          vertical_span options[:vertical_span]
        }

        on_widget_selected {
          @presenter.press(command)
        }
      }
    end

    def display_about_dialog
      message_box(body_root) {
        text 'About'
        message "Glimmer - Calculator #{VERSION}\n#{LICENSE}"
      }.open
    end

  end
end
```

Glimmer app on the desktop (using the `glimmer-dsl-swt` gem):

![](i/glimmer-cs-calculator-screenshot-linux.png)




Glimmer app on the web (using `glimmer-dsl-opal` gem):

Start the rails server:
```
rails s
```

Visit `http://localhost:3000`
(or visit: <http://glimmer-cs-calculator-server.herokuapp.com>)

You should see "Glimmer Calculator"

[![](i/glimmer-cs-calculator-screenshot-opal.png)](http://glimmer-cs-calculator-server.herokuapp.com)

Here is an Apple Calculator CSS themed version (with [CSS only](https://github.com/AndyObtiva/glimmer-cs-calculator/blob/master/server/glimmer-cs-calculator-server/app/assets/stylesheets/welcomes_apple.scss), no app code changes):

Visit <http://glimmer-cs-calculator-server.herokuapp.com/welcomes/apple>

[![](i/glimmer-cs-calculator-screenshot-opal-apple.png)](http://glimmer-cs-calculator-server.herokuapp.com/welcomes/apple)

Here is an Tiles Calculator CSS themed version (with [CSS only](https://github.com/AndyObtiva/glimmer-cs-calculator/blob/master/server/glimmer-cs-calculator-server/app/assets/stylesheets/welcomes_tiles.scss), no app code changes):

Visit <http://glimmer-cs-calculator-server.herokuapp.com/welcomes/tiles>

[![](i/glimmer-cs-calculator-screenshot-opal-tiles.png)](http://glimmer-cs-calculator-server.herokuapp.com/welcomes/tiles)




## Find Out More

### References

- Home :: [github.com/AndyObtiva/glimmer-dsl-opal](https://github.com/AndyObtiva/glimmer-dsl-opal)
- Gem :: [glimmer-dsl-opal](https://rubygems.org/gems/glimmer-dsl-opal)
- Docs :: [glimmer-dsl-opal](https://rubydoc.info/gems/glimmer-dsl-opal)
- Blog :: [Glimmer Tetris in One Day! and Many More Glimmer Articles](http://andymaleh.blogspot.com/search/label/Glimmer)
- Video :: [Whatever Happened to Desktop Development in Ruby?, MountainWest RubyConf 2011](https://confreaks.tv/videos/mwrc2011-whatever-happened-to-desktop-development-in-ruby)

