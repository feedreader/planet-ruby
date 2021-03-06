# Week 8 - props gem - yet another config (INI) reader in Ruby


Let's say you're looking for an easy configuration file format for your tool or service.
Why not use the Windows-inspired INI format as an (easier and simpler) alternative to the popular JSON, YAML
and TOML formats? Example:

`ruby.conf`:

~~~
title = Planet Ruby

[rubylang]
  title = Ruby Lang News
  link  = http://www.ruby-lang.org/en/news
  feed  = http://www.ruby-lang.org/en/feeds/news.rss

[rubyonrails]
  title = Ruby on Rails News
  link  = http://weblog.rubyonrails.org
  feed  = http://weblog.rubyonrails.org/feed/atom.xml

[viennarb]
  title = Vienna.rb News
  link  = http://vienna-rb.at
  feed  = http://vienna-rb.at/atom.xml
~~~

Now all that's missing is a gem that reads in the Windows-inspired INI format and returns a plain "old" Ruby hash.

## What's the props gem?

Using the props gem let's you read in configuration settings in the Windows-inspired INI format.
Use the - surprise, surprise - `INI` class to get started. Example:

~~~
require 'pp'
require 'props'

hash = INI.load_file( './ruby.conf' )

puts "hash:"
pp hash
~~~

Will print:

~~~
hash:
{"title"=>"Planet Ruby",
 "rubylang"=>
  {"title"=>"Ruby Lang News",
   "link"=>"http://www.ruby-lang.org/en/news",
   "feed"=>"http://www.ruby-lang.org/en/feeds/news.rss"},
 "rubyonrails"=>
  {"title"=>"Ruby on Rails News",
   "link"=>"http://weblog.rubyonrails.org",
   "feed"=>"http://weblog.rubyonrails.org/feed/atom.xml"},
 "viennarb"=>
  {"title"=>"Vienna.rb News",
   "link"=>"http://vienna-rb.at",
   "feed"=>"http://vienna-rb.at/atom.xml"}}
~~~

To access any settings works like any "standard" hash because it's just a "standard" hash.
Use `hash['rubylang']` and `hash['rubylang']['title']` and so on. Example:

~~~
puts "rubylang:"
pp hash['rubylang']
# => {"title"=>"Ruby Lang News",
      "link"=>"http://www.ruby-lang.org/en/news",
      "feed"=>"http://www.ruby-lang.org/en/feeds/news.rss"}

puts "viennarb:"
pp hash['viennarb']
# => {"title"=>"Vienna.rb News",
      "link"=>"http://vienna-rb.at",
      "feed"=>"http://vienna-rb.at/atom.xml"}

puts "rubylang/title: #{hash['rubylang']['title']}"
# => rubylang/title: Ruby Lang News

puts "viennarb/title: #{hash['viennarb']['title']}"
# => viennarb/title: Vienna.rb News
~~~



## Manage Settings Hierachies (e.g. Work, Home, Defaults, etc.) with the 'Props' class

If you prefer you can wrap the hash in a `Props` class. Example:

~~~
props = Props.new( hash, 'ruby.ini' )

puts "rubylang:"
pp props.get('rubylang')

puts "viennarb:"
pp props.get('viennarb')

puts "rubylang/title: #{props.get_from_section('rubylang','title')}"
# => rubylang/title: Ruby Lang News

puts "viennarb/title: #{props.get_from_section('viennarb','title')}"
# => viennarb/title: Vienna.rb News
~~~

What's the point you might ask? Using the `Props` class you can linkup hash settings
into a lookup hierachy. Example:

~~~
default_props = Props.new( defaults_hash, 'DEFAULTS' )
home_props    = Props.new( home_hash,     '~/ruby.conf', default_props )
props         = Props.new( work_hash,     './ruby.conf', home_props)
~~~

Now if you try `props.get('viennarb')`, for example, the getter will first
look in the working (current) folder settings hash
and than in the home folder settings hash and finally if still not found in the defaults hash.
For a "real-world" example lets wrap-up with the config reader snippet from the markdown gem
using the `Props` class. Example:

~~~
class Config

  DEFAULTS = { 'libs' => [ 'kramdown' ],
               'extnames' => [
                 '.markdown',
                 '.m',
                 '.mark',
                 '.mkdn',
                 '.md',
                 '.mdown',
                 '.markdn',
                 '.txt',
                 '.text' ],
                'redcarpet' => {
                 'extensions' => [
                    'no_intra_emphasis',
                    'fenced_code_blocks',
                    'tables',
                    'strikethrough' ] }
             }

  def initialize
    @props = @props_default = Props.new( DEFAULTS, 'DEFAULTS' )

    ## check for user settings in home folder

    props_home_file = File.join( Env.home, 'markdown.conf' )
    if File.exists?( props_home_file )
      puts "Loading settings from '#{props_home_file}'..."
      @props = @props_home = Props.load_file( props_home_file, @props )
    end

    ## check for user settings in working (current) folder

    props_work_file = File.join( '.', 'markdown.conf' )
    if File.exists?( props_work_file )
      puts "Loading settings from '#{props_work_file}'..."
      @props = @props_work = Props.load_file( props_work_file, @props )
    end
  end

  def markdown_extnames
    @props.get( 'extnames' )
  end

  ...

end
~~~


## Find Out More

* home     :: [github.com/rubylibs/props](https://github.com/rubylibs/props)
* gem      :: [rubygems.org/gems/props](https://rubygems.org/gems/props)
* rdoc     :: [rubydoc.info/gems/props](http://rubydoc.info/gems/props)
