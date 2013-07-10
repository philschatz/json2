## Reasons to Use JSON

1.  JSON is more compact, meaning smaller file sizes to send to a client
2.  JSON is a strict standard, so there's less possibility of ambiguity or exceptions
3.  JSON is **much** faster to parse than XML, and you don't need to write any custom code to parse it
    1.  Current code to parse a book (already broken with new COLLXML format, and code complexity increases exponentially with more features):
          `````
          parseHTML = (html) ->
            if typeof html isnt 'string' then return []

            results = []

            $(html).find('> ol').find('> li').each (index, el) ->
              $el = $(el)
              $node = $el.children().eq(0)

              if $node.is('a')
                id = $node.attr('href')
                title = $node.text()

              # Only remember the title if it's overridden
              if not title or $node.hasClass('autogenerated-text')
                results.push({id: id})
              else
                results.push({id: id, title: title})

            return results
          `````

    2.  No code is required to parse JSON, since support is built-in to Backbone, but if you needed to, it would always be one line:
        ```JSON.parse(string)``` in JavaScript
        In Python, just ```import json``` and then ```json.loads(string)```
3.  JSON, unlike XML, matches the data model of most programming languages
    1.  Literally "JavaScript Object Notation", it can be serialized and parsed back into an object in any modern browser
    2.  Maps easily to Python as well: Object = Dictionary, Array = List, etc.
4.  Support for JSON has only been growing as it is becoming the default data exchange format for the web
5.  PostgreSQL has built-in support for JSON
    1.  http://www.postgresql.org/docs/devel/static/datatype-json.html
    2.  http://www.postgresql.org/docs/9.3/static/functions-json.html
6.  Backbone.js is designed to work with JSON
    1.  "Backbone.js gives structure to web applications ... and connects it all to your existing API over a RESTful **JSON** interface."

