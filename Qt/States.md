## States in Qt

States allow you to define configuration of items. 
All items have a default state that defines the default configuration of objects and property values. New states can be defined by adding **State** items to the **states** property to allow items to switch between different configurations.

**states** is a property that hold a list of possible states for an item. To change the state of any item, we set the state property to one of the values that it holds.

```cpp
  rect1.state = "onClickedState"
```

### Example Code

```qt
import QtQuick 2.12
Rectangle{
    id:root
    width: 500
    height: 700

    Rectangle{
        id: r1
        color: "black"
        width: 200
        height: 400
        anchors.centerIn: parent
    }
    MouseArea{
        id: mouseArea
        anchors.fill : parent
        onClicked: (root.state == 'clicked')?root.state = "":root.state = "clicked";
    }
    states: [
        State{
            name: "clicked"
            PropertyChanges{
                target: r1
                color: "red"
            }
        }
    ]
}

```

If you just have a single state, you may also define it as:
```qt

  states: State{
    
    //properties

  }
```

[Refer](https://doc.qt.io/qt-5/qml-qtquick-state.html#details)