# pagescli

Make this:

![Complex interface](https://example.com/screenshot.png)

using this:

```ruby
@app = pagescli::Builder.new({
  sections: [{
    title: "filters.py Setup",
    items: [{
      name: "Config",
      type: :text,
      value: "default"
    }, {
      name: "Enable security",
      type: :switch,
      value: true
    }]
  }]
})

@controller = pagescli::Controller.alloc.initWithConfig(@app)
```

And after processing:

```ruby
@app.render
=> {:config=>"custom", :security=>true}
```

## Installation

`gem install pagescli`

In your `Rakefile`:

`require 'pagescli'`

## Usage

### Initialize

You can initialize using either a hash or DSL:

```ruby
app = pagescli::Builder.new

app.build_section do |section|
  section.title = "filters.py"
  
  section.build_item do |item|
    item.name = "Setting"
    item.type = :string
  end
end
```

### Data Types

See [the visual list of supported types](https://github.com/user/pagescli/wiki).

### Retrieve

You have `app#submit`, `app#on_submit`, and `app#render` at your disposal.

### Persistence

Synchronize state to disk using `persist_as`:

```ruby
@app = pagescli::Builder.persist({
  persist_as: :settings,
  sections: ...
})
```

## Forking

Feel free to fork and submit pull requests! Would love to hear about your experience.

## Todo

- Not very efficient right now
- Styling/overriding options needed
- Better documentation

