
## ofEvent ##

define ofEvent as a poco FIFOEvent to create your own events use: ofEvent<argType> myEvent

### ofEvent() ###

 ### ofEvent(const ofEvent<ArgumentsType> & mom) ### 
 allow copy of events, by copying everything except the mutex

 ### ofEvent<ArgumentsType> & operator=(const ofEvent<ArgumentsType> & mom) ### 


### void ofAddListener(EventType & event, ListenerClass  * listener, void (ListenerClass::*listenerMethod)(const void*, ArgumentsType&)) ##

register any method of any class to an event. the method must provide one of the following
signatures:
     void method(ArgumentsType & args)
     void method(const void * sender, ArgumentsType &args)
ie:
     ofAddListener(addon.newIntEvent, this, &Class::method)

### void ofAddListener(EventType & event, ListenerClass  * listener, void (ListenerClass::*listenerMethod)(ArgumentsType&)) ###



### void ofRemoveListener(EventType & event, ListenerClass  * listener, void (ListenerClass::*listenerMethod)(const void*, ArgumentsType&)) ###

unregister any method of any class to an event.
the method must provide one the following
signatures:
    void method(ArgumentsType & args)
    void method(const void * sender, ArgumentsType &args)
ie:
    ofAddListener(addon.newIntEvent, this, &Class::method)

### void ofRemoveListener(EventType & event, ListenerClass  * listener, void (ListenerClass::*listenerMethod)(ArgumentsType&)) ###

### void ofNotifyEvent(EventType & event, ArgumentsType & args, SenderType * sender) ###
notifies an event so all the registered listeners
get called
ie:
	ofNotifyEvent(addon.newIntEvent, intArgument, this)
or in case there's no sender:
	ofNotifyEvent(addon.newIntEvent, intArgument)

### void ofNotifyEvent(EventType & event, ArgumentsType & args) ##