!SLIDE bullets swipe
# View

* Organizes the View
* Controller/ View in traditional MVC
* Listens to models
* Renders the views
* Can use template libraries

!SLIDE smaller code
# View

    @@@javascript
    LocalizationEditor = Backbone.View.extend({
      tagName: 'li',
      className: 'localization-editor',

      events: {
        'change input': 'setField'
      },

      initialize: function() {
        _.bindAll(this, 'render');
        this.model.bind('change:translations', this.render);
      },


!SLIDE smaller code execute
# View (el)

    @@@javascript
    LocalizationEditor = Backbone.View.extend({
      tagName: 'li',
      className: 'localization-editor'
    });

    editor = new LocalizationEditor();
    alert(editor.el + ' ' );

!SLIDE small code
# View (.$)

    @@@javascript
    Gui.Chapter = Backbone.View.extend({
      serialize : function() {
        return {
          title: this.$(".title").text(),
          start: this.$(".start-page").text(),
          end:   this.$(".end-page").text()
        };
      }
    });

!SLIDE smaller code execute
# View (render)

    @@@javascript
    var Bookmark = Backbone.View.extend({
      initialize: function() {
        _.bindAll(this, 'render');
      },
      render: function() {
        // The template method comes from underscore
        $(this.el).html(this.template(this.model.toJSON()));
        return this;
      }
    });

!SLIDE small code execute
# View Underscore `_.template`

    @@@javascript
    var compiled = _.template("hello: <%= name %>");
    result = compiled({name : 'moe'});

    
!SLIDE smaller code 
# View (events)
    
    @@@javascript
    var DocumentView = Backbone.View.extend({
      events: {
        "dblclick"                : "open",
        "click .icon.doc"         : "select",
        "contextmenu .icon.doc"   : "showMenu",
      },

      open: function() {
        window.open(this.model.get("viewer_url"));
      },

      select: function() {
        this.model.set({selected: true});
      },
      ...
    });

!SLIDE smaller bullets
# Events

* "add" (model, collection) — added to collection
* "remove" (model, collection) — removed from collection
* "reset" (collection) — collection replaced
* "change" (model, collection) —  model attributes changed.
* "change:[attribute]" (model, collection) — specific attribute changed
* "destroy" (model, collection) — model is destroyed.
* "error" (model, collection) —  model validation fails, or save call fails
* "route:[name]" (router) — router's routes has matched.
* "all" — any triggered event, event name as the first argument.


!SLIDE smaller
# View Binding
    
    @@@javascript
    var MessageList = Backbone.View.extend({

      initialize: function() {
        var messages = this.collection;
        messages.bind("reset", this.render, this);
        messages.bind("add", this.addMessage, this);
        messages.bind("remove", this.removeMessage, this);
      }

    });

!SLIDE small 
# View bindAll
    
    @@@javascript
    var MessageList = Backbone.View.extend({

      initialize: function() {
        _.bindAll(this, 'render', 'renderOne');
      }

      render: function() {},
      renderOne: function() {}

    });

!SLIDE small
# View bindAll not
    
    @@@coffeescript
    # Coffeescript
    class MessageList extend Backbone.View

      render: =>

      renderOne: =>
        

