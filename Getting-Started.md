This page provides all the necessaries to implement <b>BEMSimpleLineGraph</b> to your project, and to draw your first graph!
<a name='Installation'/>
##Installation
###CocoaPods
The easiest way to install <b>BEMSimpleLineGraph</b> is to use <a href="http://cocoapods.org/" target="_blank">CocoaPods</a>. To do so, simply add the following line to your `Podfile`:  

    pod 'BEMSimpleLineGraph'

###Manual Installation	
The other way to install <b>BEMSimpleLineGraph</b>, is to drag and drop the *Classes* folder into your Xcode project. When you do so, check the "*Copy items into destination group's folder*" box.

***

<a name='Set-up'/>
##Set-up
Setting up <b>BEMSimpleLineGraph</b> in your project is simple. If you're familiar with UITableView, then <b>BEMSimpleLineGraph</b> should be a breeze. Follow the steps below to get everything up and running.

 1. Import `"BEMSimpleLineGraphView.h"` to the header of your view controller:

         #import "BEMSimpleLineGraphView.h"

 2. Implement the `BEMSimpleLineGraphDelegate` and the `BEMSimpleLineGraphDataSource` to the same view controller:

         @interface YourViewController : UIViewController <BEMSimpleLineGraphDelegate, BEMSimpleLineGraphDataSource>

 3.  BEMSimpleLineGraphView can be initialized in one of two ways. You can either add it directly to your interface (storyboard file) OR through code. Both ways provide the same initialization, just different ways to do the same thing. Use the method that makes sense for your app or project.

     **Interface Initialization**  
     1 - Add a UIView to your UIViewController  
     2 - Change the class type of the UIView to `BEMSimpleLineGraphView`  
     3 - Link the view to your code using an `IBOutlet`. You can set the property to `weak` and `nonatomic`.  
     4 - Select the Connect the `BEMSimpleLineGraphView` in your interface. Connect the delegate and dataSource properties to your ViewController.  
     5 - Select the `BEMSimpleLineGraphView` and open the Attributes Inspector. Most of the line graph's customizable properties can easily be set from the Attributes Inspector. The Sample App demonstrates this capability. Note that graph data will not be loaded in Interface Builder.  

     **Code Initialization**  
     Just add the following code to your implementation (usually the `viewDidLoad` method).

         BEMSimpleLineGraphView *myGraph = [[BEMSimpleLineGraphView alloc] initWithFrame:CGRectMake(0, 0, 320, 200)];
         myGraph.delegate = self;
         myGraph.dataSource = self;
         [self.view addSubview:myGraph];

 4. Implement the two required methods: `numberOfPointsInLineGraph:` and `lineGraph:valueForPointAtIndex:`:

  **Number of Points in Graph**  
  Returns the number of points in the line graph. The line graph gets the value returned by this method from its data source and caches it.

      - (NSInteger)numberOfPointsInLineGraph:(BEMSimpleLineGraphView *)graph {
      		return X; // Number of points in the graph.
      }

  **Value for Point at Index**  
  Informs the position of each point on the Y-Axis at a given index. This method is called for every point specifed in the `numberOfPointsInLineGraph:` method. The parameter `index` is the position from left to right of the point on the X-Axis:

  	  - (CGFloat)lineGraph:(BEMSimpleLineGraphView *)graph valueForPointAtIndex:(NSInteger)index {
      	 	  return …; // The value of the point on the Y-Axis for the index.
  	  }