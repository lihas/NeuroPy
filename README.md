NeuroPy
=======

NeuroPy library written in python to connect, interact and get data from __neurosky's MindWave__ EEG headset.

This library is based on the minwave mindset communication protocol published by [Neurosky](http:://neurosky.com) and is tested
with Neurosky Mindwave EEG headset.

##Installation##

1. Download the source distribution (zip file) from [dist directory](https://github.com/lihas/NeuroPy/tree/master/dist)
2. unzip and navigate to the folder containing _setup.py_ and other files
3. run the following command:
    `python setup.py install`

##Usage##

1. Importing the module: `from NeuroPy import NeuroPy`

1. Initialising: `object1=NeuroPy("COM6",57600)` _#windows_ <br /> `object1=NeuroPy("/dev/rfcomm0",57600)` _#linux_

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

##Sample Program##
    
    from NeuroPy import NeuroPy
    object1=NeuroPy("COM6") #If port not given 57600 is automatically assumed
                            #object1=NeuroPy("/dev/rfcomm0") for linux
    def attention_callback(attention_value):
        "this function will be called everytime NeuroPy has a new value for attention"
        print "Value of attention is",attention_value
        #do other stuff (fire a rocket), based on the obtained value of attention_value
        #do some more stuff
        return None
    
    #set call back:
    object1.setCallBack("attention",attention_callback)
    
    #call start method
    object1.start()
    
    while True:
        if(object1.meditation>70): #another way of accessing data provided by headset (1st being call backs)
            object1.stop()         #if meditation level reaches above 70, stop fetching data from the headset
