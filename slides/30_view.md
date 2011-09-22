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

!SLIDE smaller code execute
# View (render)

    @@@javascript
    var Bookmark = Backbone.View.extend({
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

!SLIDE small code
# View (.$)

    @javascript
    ui.Chapter = Backbone.View.extend({
      serialize : function() {
        return {
          title: this.$(".title").text(),
          start: this.$(".start-page").text(),
          end:   this.$(".end-page").text()
        };
      }
    });

    
!SLIDE smaller code execute
# View (events)
    
    @@@javascript
    var DocumentView = Backbone.View.extend({
      events: {
        "dblclick"                : "open",
        "click .icon.doc"         : "select",
        "contextmenu .icon.doc"   : "showMenu",
      },

      render: function() {
        $(this.el).html(this.template(this.model.toJSON()));
        return this;
      },

      open: function() {
        window.open(this.model.get("viewer_url"));
      },

      select: function() {
        this.model.set({selected: true});
      },
      ...
    });


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


    


