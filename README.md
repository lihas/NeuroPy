NeuroPy
=======

NeuroPy library written in python to connect, interact and get data from __neurosky's MindWave__ EEG headset.

This library is based on the minwave mindset communication protocol published by [Neurosky](http:://neurosky.com) and is tested
with Neurosky Mindwave EEG headset.

##Usage##

1. Initialising: object1=NeuroPy("COM6",57600) _#windows_

1. After initialising , if required the callbacks must be set
then using the start method the library will start fetching data from mindwave
i.e. `object1.start()`
similarly stop method can be called to stop fetching the data
i.e. `object1.stop()`

###The data from the device can be obtained using either of the following methods or bot of them together:###
    
* Obtaining value: `variable1=object1.attention` _\#to get value of attention_
    >__\#other variables:__ attention,meditation,rawValue,delta,theta,lowAlpha,highAlpha,lowBeta,highBeta,lowGamma,midGamma, poorSignal and blinkStrength
    
* Setting callback:a call back can be associated with all the above variables so that a function is called when the variable is updated. Syntax: `setCallBack("variable",callback_function)` <br />
    __for eg.__ to set a callback for attention data the syntax will be `setCallBack("attention",callback_function)`
    
    >__\#other variables:__ attention,meditation,rawValue,delta,theta,lowAlpha,highAlpha,lowBeta,highBeta,lowGamma,midGamma, poorSignal and blinkStrength
