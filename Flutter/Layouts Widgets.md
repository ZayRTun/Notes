# Single-Child Layout Widgets  

## Container 
- A convenience widget that combines common painting, positioning, and sizing widgets.
- Containers with no children try to be as big as possible unless the incoming constraints are unbounded, in which case they try to be as small as possible. Containers with children size themselves to their children. The `width`, `height`, and [constraints](https://api.flutter.dev/flutter/widgets/Container/constraints.html) arguments to the constructor override this.  



# Multi-Child Layout Widgets  

## Column
- A widget that displays its children in a vertical array.
- The [Column](https://api.flutter.dev/flutter/widgets/Column-class.html) widget does not scroll (and in general it is considered an error to have more children in a [Column](https://api.flutter.dev/flutter/widgets/Column-class.html) than will fit in the available room). If you have a line of widgets and want them to be able to scroll if there is insufficient room, consider using a [ListView](https://api.flutter.dev/flutter/widgets/ListView-class.html).
- For a horizontal variant, see [Row](https://api.flutter.dev/flutter/widgets/Row-class.html).
- If you only have one child, then consider using [Align](https://api.flutter.dev/flutter/widgets/Align-class.html) or [Center](https://api.flutter.dev/flutter/widgets/Center-class.html) to position the child.
- It tries to as much space as possible vertically 
- But horizontally it's limiting it self to the size of it's children.
- We can change it's vertical behavior by setting   
- Note: The main axis of `Column` is vertical

**Spacing in between children of the container**
- `SizedBox(height: 10.0)`
- Creates a fixed size box. The [width] and [height] parameters can be null to indicate that the size of the box should not be constrained in the corresponding dimension.

**Properties**
- `mainAxisAlignment:`
	- `mainAxisAlignment: MainAxisAlignment.center`
	- **Options: ** `start, center, end, spaceAround, spaceBetween, spaceEvenly`
	- How the children should be placed along the main axis in a flex layout.
- `mainAxisSize:`
	- `mainAxisSize: MainAxisSize.min`
- `verticalDirection`
	- A direction in which boxes flow vertically.
	- This is used by the flex algorithm (e.g. [Column]) to decide in which direction to draw boxes.
	- `verticalDirection: VerticalDirection.up`
		- Will arrange children from bottom to top
	- `verticalDirection: VerticalDirection.down`
		- Will arrange children from top to bottom. **Default Behavior**
- `crossAxisAlignment:`
	- `crossAxisAlignment: CrossAxisAlignment.end`
	- **Options: ** `stretch`
		- Require the children to fill the cross axis.
		- This causes the constraints passed to the children to be tight in the cross axis. 
	- How the children should be placed along the cross axis in a flex layout.
	```dart
	Container(
		width: double.infinity, // will fill the container horizontally as wide as possible
		height: 10,
	)
	```



## Row
- Layout a list of child widgets in the horizontal direction.
- To cause a child to expand to fill the available horizontal space, wrap the child in an [Expanded](https://api.flutter.dev/flutter/widgets/Expanded-class.html) widget.
- The [Row](https://api.flutter.dev/flutter/widgets/Row-class.html) widget does not scroll (and in general it is considered an error to have more children in a [Row](https://api.flutter.dev/flutter/widgets/Row-class.html) than will fit in the available room). If you have a line of widgets and want them to be able to scroll if there is insufficient room, consider using a [ListView](https://api.flutter.dev/flutter/widgets/ListView-class.html).
**Functionally `Row <Widget>` works the same as the `Column <Widget>` but opposite**

