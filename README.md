# EventKit
Closure based Event library

<img width="100" alt="img" src="https://rawgit.com/stylekit/img/master/EventLib.svg">

- Small footprint: Only 2 methods and a variable
- Propagates up class hierarchies. That extend the EventSender
- Basic event concept: EventHandler, Event, EventSender
- Determine where the event came from with origin and immediate

Simple Example:  
```swift
class A:EventSender{
    func doSomething(){
        onEvent(Event(Event.update,self))
    }
}
var a = A()
func onSomeEvent(event:Event){/*<--Event handler*/
    if event.assert(.update,origin:a){
        print("something happened on: \(event.origin) for event type: \(event.type)")
    }
}
a.event = onSomeEvent
a.doSomething()//Output: something happened on: A for event type: eventUpdate
```

Read about the event system here: http://stylekit.org/blog/2016/02/10/The-event-system/  
