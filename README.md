# dock-spawn-ts
A TypeScript Version of dock-spawn (see https://github.com/coderespawn/dock-spawn)

# info
it is still alpha, npm packages will follow in the next few weeks

# how to use:
(needs to be changed for typescript)
```javascript
    // Convert a div to a dock manager.  Panels can then be docked on to it
    dockManager = new DockManager(query("#my_dock_manager"));
    dockManager.initialize();

    // Let the dock manager element fill in the entire screen
    window.on.resize.add(onResized);
    onResized(null);

    // Convert existing elements on the page into "Panels". 
    // They can then be docked on to the dock manager 
    // Panels get a titlebar and a close button, and can also be 
    // converted to a floating dialog box which can be dragged / resized 
    var solution = new PanelContainer(query("#solution_window"), dockManager);
    var output = new PanelContainer(query("#output_window"), dockManager);
    var properties = new PanelContainer(query("#properties_window"), dockManager);
    var toolbox = new PanelContainer(query("#toolbox_window"), dockManager);
    var outline = new PanelContainer(query("#outline_window"), dockManager);
    var problems = new PanelContainer(query("#problems_window"), dockManager);
    var editor1 = new PanelContainer(query("#editor1_window"), dockManager);
    var editor2 = new PanelContainer(query("#editor2_window"), dockManager);

    // Dock the panels on the dock manager
    DockNode documentNode = dockManager.context.model.documentManagerNode;
    DockNode solutionNode = dockManager.dockLeft(documentNode, solution, 0.20);
    DockNode outlineNode = dockManager.dockFill(solutionNode, outline);
    DockNode propertiesNode = dockManager.dockDown(outlineNode, properties, 0.6);
    DockNode outputNode = dockManager.dockDown(documentNode, output, 0.4);
    DockNode problemsNode = dockManager.dockRight(outputNode, problems, 0.40);
    DockNode toolboxNode = dockManager.dockRight(documentNode, toolbox, 0.20);

    DockNode editor1Node = dockManager.dockFill(documentNode, editor1);
    DockNode editor2Node = dockManager.dockFill(documentNode, editor2);
```
