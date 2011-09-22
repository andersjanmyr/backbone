!SLIDE bullets
# Collection

* Collection of models
* Fires add, remove, and change events
* Fetches a collection from the server

!SLIDE code small
# Collection

    @@@javascript
    var Library = Backbone.Collection.extend({
      model: Book
    });



!SLIDE code small execute
# Collection toJSON

    @@@javascript
    var collection = new Backbone.Collection([
      {name: "Tim", age: 5},
      {name: "Ida", age: 26},
      {name: "Rob", age: 55}
    ]);

    result = collection.toJSON();

!SLIDE code smaller
# Underscore methods

    @@@javascript
    forEach (each), map, reduce (foldl, inject),
    find (detect), filter (select), reject, every (all)
    some (any), include, invoke, max, min, sortBy, groupBy
    sortedIndex, toArray, size, first, rest, last, without
    indexOf, lastIndexOf, isEmpty, chain,  reduceRight (foldr)

!SLIDE code small
# Collection Persistence

    @@@javascript
    var book = Library.get(110);
    
    // Fires add event
    ships.add([
      {name: "Flying Dutchman"},
      {name: "Black Pearl"}
    ]);

    // Fires remove event
    collection.remove(models, [options])

!SLIDE code small
# Collection Persistence

    @@@javascript
    // Fires reset event
    products.reset[{name: 'Kjell'}, {name: 'Arne'}])

    // Fetches from the server, fires reset event
    products.fetch()

    // Create a new model and adds it
    var othello = NYPL.create({
      title: "Othello",
      author: "William Shakespeare"
    });

