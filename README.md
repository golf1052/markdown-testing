#### HueBridge Class
Let's start with the `[HueBridge]` class. Use this to get an APIKey/username from your bridge so you can get and set light data with it using the `[HueLight]` class later.
 1. Get the IP address of your Bridge. The `[HueBridge]` class contains a static method (this means you can call it without instantiating the class) called `.FindHueBridge()`.
 2. Run
 
 ```powershell
 [HueBridge]::FindHueBridge()
 ```
 3. Your computer will perform a search. The search is synchronous (means you need to wait for it to complete) and takes about 15-20 seconds to finish. The method finds all UPnP devices described as "Hue" on your LAN (Subnet) and returns those as a list, giving you the IP of your bridge. One might argue this should happen by default, after all, the Hue Bridge IP address may change in a DHCP network. Two reasons why I don't do this automagically: 1. Who says this is the only Hue Bridge in the network? 2. The method call is a blocking action and I've not tried to get PowerShell to do stuff asynchronously with a callback yet.
 4. Instantiate a `[HueBridge]` class using your discovered (or known) Bridge IP address. Substitue your own bridge's IP address obviously.
 
 ```powershell
 $Bridge = [HueBridge]::New('192.168.1.12')
 ```
 5. Get the properties of the Bridge object.
 
 ```powershell
 $Bridge
 ```
 6. You'll see just the IP address property for now.
