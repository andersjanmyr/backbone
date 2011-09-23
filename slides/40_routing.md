!SLIDE small
# Routing

* Maps routes to functions
* Maps functions to routes


!SLIDE small
# Routing Example
    
    @@@javascript
    var SearchRouter = Backbone.Router.extend({

      routes: {
        "help":                 "help",    // #help
        "search/:query":        "search",  // #search/kiwis
        "search/:query/p:page": "search"   // #search/kiwis/p7
      },

      help: function() { },

      search: function(query, page) { ...  }
    });

    Backbone.history.start();

!SLIDE small
# Routing routes
    
    @@@javascript
    routes: {
      "help/:page":         "help",
      "download/*path":     "download",
      "folder/:name":       "openFolder",
      "folder/:name-:mode": "openFolder"
    }

!SLIDE small
# Routing navigation

    @@@javascript
    openPage: function(pageNumber) {
      // Open the page
      this.document.pages.at(pageNumber).open();
      // Update the history
      this.navigate("page/" + pageNumber);
    }

    // Or make the router call the defined action
    this.navigate("page/" + pageNumber, true);
