# 8.1 iOS

- 
## Cocoapods with local path

    Requirement : [CocoaPods](https://cocoapods.org/) 

    After pod **version > 1.0**, you need to identify the target. Create 'Podfile' in project root folder :
    ```
 target 'MyiOSApp' do 
	pod 'React', :path => '../../AwesomeProject/node_modules/react-native', :subspecs => [
  	  'Core',
  	  'RCTImage',
  	  'RCTNetwork',
  	  'RCTText',
  	  'RCTWebSocket',
	]
  end
    ```
    
  then ```pod install```
  
  ![](pod_integration.png)
  
  


    

    
    