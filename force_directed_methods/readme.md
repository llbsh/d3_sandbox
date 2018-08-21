# Force Directed Method (from Lecture wk3)

## A minimun example:
[from D3 in Depth book](http://d3indepth.com/force-layout/)

### How to setup a force simulation in D3?

There are four steps:
* create an array of objects. 
* call `forceSimulation` passing the array of objects. 
* add one or more force function
    * `forceManyBody`: make the elements repel or attract each other. Param: .strength() define the length or the force. strength(+) attract, strength(-) repel. default -30
    * `forceCenter`: attracts the elements towards a center. Parameter is x, y, the coordinates of the center.  
    * `forceCollidde`: stop elements overlapping and is quite useful. must specify the radius of the elements using `.radius()` eg:

    ```javascript
      .force('collision', d3.forceCollide().radius(function(d) {
    return d.radius
      })
    ```
    * `forceX` and `forceY`: cause elements to be attracted towards X or Y.

    ```javascript
    simulation.force('x', d3.forceX().x(function(d) {
        return xCenter[d.category];
    }))
    ```
    * `forceLink` push linked elements to be a fixed distance apart. It requries an array of links ( link specifies which elements are linked together. ).


* Setup a callback function to update the elements positions after each tick. Each time, the simulation iterates, then ticked() callback function will be called. 



Learn the example from [mbostock](https://bl.ocks.org/mbostock/4062045)


### Other notes:

Generate some random data. 
```javascript

var nodes = d3.range(numNodes).map(function (d, i) {
            return {
                radius: Math.random() * 25,
                category: i % 3
            }
        });
```

append() circle() merge()?? what does merge do??  @TODO.