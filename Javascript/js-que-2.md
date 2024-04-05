1. What is js?
2. explain the difference between let,const and var
3. how does hoisting work in js?
4. describe the conecept of clousures
5. explain the event loop in js
6. what is the difference between == and ===
7. how do you check the type  of a variable in js?
8. what is the use of the this keyword in js?
9. explain the difference between function declaration and function expression
10. how does the setTimeout function work?
11. what is a callback function?
12. explain the concept of pure function
13. describe the difference between funcion.call, function.apply, function.bind
14. what is the purpose of the arguments object in a function?
15. how do you create a closure in js?
16. what is the use of the bind method?
17. what is the difference between a shallow  copy and deep copy
18. how does the call stack work in javascript
19. explain the concept of function currying
20. how can you avoid callback hell in javascript
21. what is prototype in inheritance
22. how do you create and object in js
23. what is the purpose of prototype property in js
24. explain the difference between Object.create and the constructor pattern
25. how do you add a property to an object in js
26. what is the hasOwnProperty to an object in js
27. how can you prevent modification of object properties in js
28. describe the use of the new keyword
29. explain the concept of object destructuring in js
30. what is difference between null and undefined
31. what is the DOM
32. how do you select elements with vanilla js
33. explain event delegation in js
34. what is the purpose of the addEventListener method
35. how do you create and remove elements in the DOM
36. explain the concept of event propagation
37. how can you prevent the default behaviour of an event
38. what is the purpose of the data-attribute in html
39. describe the difference between innerHHTML and textContent
40. how do you handle asynchronous code in js?



 

1. How Javascript works and Execution Context ?

 ```
			- Execution context is an 2 component - memory or variable envioronment 
			- contains variable and function as the key value pair. code or thread of execution - it is an whole code is executed one line at a time 2 types of JS Context
			- Global and Function(Local).
			- Javascript is a Synchronous single threaded language.
 
 ```
 					
---

2. For Each, For in, For of		


```
			** For each() -> Simply calls a provided function on each elements in your array and here doesn't return anything.

				Syntax- arr.forEach(callback (curent value[index[array]]){
					//execution
					}[thisArg]);
					
				eg- const cities= ['pune', 'mumbai','nag'];

					cities.forEach(function(city){
						c.log (	city + " => " + city.length);
					})  // pune=>4  mumbai=>6  nag=>3
					
			** for in=> Iterate and return indexes for all elements of an array.

						for(var city in cities){
							c.log(city + " => " + city.length);
						} // 0 => 1 1=>1 2=>1
						
			** for of => return element of an array; 

						for(var city of cities){
							c.log(city + " => " + city.length);
						} // pune=> 4 mumbai=>6 nag=>3
```
				  
---

3. Undefined vs not defined ?
Ans-  
		console.log(x); // hoisting - undefined
		var x= 7 ; 
		var b;
		console.log(b); //undefined
		
		console.log(a); // a is not defined , we are not declared  a variable this is get not defined.


---				  

 4. Synchronous and Asynchronous in js ?
Ans-  Js is a Synchronous and single threaded language.
		Synchronous code is executed in sequence- each statement waits for the previous statement to finish before executing.
		Synchronous operation block instructions until the task is completed.
		
	  Js execution envioronment is Asynchronous.
		  Asynchronous code doesn't have to wait - your program can continue to run.
		  Asynchronous operation can execute without blocking other operations.
		  

---
			
5. Function Statement vs Function expression?
Ans- measure difference is hoisting .

		ex- a(); //a called
			b(); // typeerror: b is not function
			
			function a(){
			  console.log("a called");
			} // func statement or func declaration
			
			var b = function(){
			   console.log("b called");
			} //func expression 
			
			var c = function xyz(){
			   console.log("c called");
			} //Named func expression 
			
			c(); // c called
			xyz(); // reference error: xyz is not defined
			
	**Anonymous function- without a name this is anonymous func, nd this func does not have own identity, getting syntax error.
				ex-  function(){//exexution}
			what is use anonymous func- when the function are used as a value
	
	**First class function - the ability of a function to be used as values and can be passed as a argumrnt to the another function nd can be returned from the function this ability is called first called function.
					
---


6. SetTimeOut with Closuers in js?
Ans- SetTimeOut is take a callback function nd stores into some place and attach to the timer do it.
		Its run only once after the code execution . it is timer show in milisecond (1000).Its not wait for anythings.
		
		ex- after every seconds print value-
				function x(){
				  for(let i=1; i<=5; i++){
					setTimeout(function () {
					console.log(i);
					},i * 1000);
				  }
				  console.log("Hello");
				}
				x();
				
				
		ex- function x(){
				  for(let i=1; i<=5; i++){
					function close(x){
					setTimeout(function () {
					console.log(x);   
					},x * 1000);
					}
					close(i);
				  }
				  console.log("Hello");
				}
				x();
				
				
				
*** - Lexical Environment ?
Ans-  The Scope which is maintain a copy of outer scope variable to be used inside the nested/inner function.
		Parameter and variable of outer scope can be accessed from nested (inner) function.
		Parameter and variable of inner function can not be accessed in outer function.
		Lexical Environment that means the local memory along with lexical envioronment of the parent.(hirachy).
		
		Ex-   function f1(a){
				function f2(b){
					function f3(c){
						console.log(a,b,c);
					}
				   console.log(a,b)	;
				}
				  console,log(a);
			  }
			  

****- SetTimeOut in js?
Ans- Allow us to run the function once after interval of time .


	SetInterval : - Allow us to run a function repeatedly starting after the interval of time , then repeating continously 
					at that interval.
					
			eg- let timers = setInterval (()=> alert('tick'),2000); // repeat show alert afetr every 2 sec
			
				setTimeout (()=>{
					clearInterval(timers);
					alert('stop');
				},5000) // after 5sec auto stop.
				


***- Local storage and Session Storage  ?
Ans-Local storage-  This read-only interface property provides access to the Document’s local storage object,
		the stored data is stored across browser sessions.
	localStorage data for a document loaded in a private browsing or incognito session.
	localStorage data does not expire.
	You can keep the data store in that browser as you want long time.
		
		**Methods-   1. setItem() Method -  It is used to store the value in a particular location with the name of the key.
											localStorage.setItem(key, value)
											
					2. getItem() Method – This method  which is used to get the value stored with a particular key name.
											localStorage.getItem(key)
											
					3. removeItem() Method– This is method is used to remove the value stored in the memory in reference to key.
											localStorage.removeItem(key)
											
					4.clear() Method – This method is used to clear all the values stored in localstorage.
											localStorage.clear()						
		
	
	sessionStorage, except that sessionStorage data gets cleared when the page session ends – that is when the page is closed.
	 It is cleared when the last “private” tab of a browser is closed .
	 sessionStorage data is cleared when the page session ends.
	
	same method use in sessionStorage-  setItem(), getItem(),removeItem(), clear().
	
	
	

****- Apply(), call(), bind() ?
Ans-  The call() method calls the function with a given this value and allows passing in arguments one by one 
		separating them with commas
		
	The apply() method calls the function with a given this value and allows passing in arguments as an array 
	
	The bind() method returns a new function and allows passing in a this array and any number of arguments.


		
	
****- Split vs Join vs Splice
Ans-  Split is used to literally ‘split’ a string into an array of substrings.
		A specified separator can be used to determine the point of separation and 
			a limit can be used to determine how many splits to make. 
			
	Slice is a method of both arrays and strings. 
	For a string — the method extracts a portion of the string and returns it as a new string. 
	Similarly, for an array — the method extracts a portion of an array and returns it as a new array. 
	The method takes a beginning and ending argument. 
	
	
	Splice() can remove, replace existing elements, or add new elements to an array.
	Splice alters the existing array, but it will return the removed items in an array. 
	If there are not any removed items the return will be an empty array. 
	Splice takes 3 arguments — add, delete, update. 
	
		const month= ['Jan', 'Feb', 'March', 'April', 'May',]
		const newM = month.splice(4, 0 , Dec) ; // after april adding Dec ; 4-add , 0- dleete, Dec- add/update;
		
	



****- SET  in JavaScript ?
Ans- The Set object lets you store unique values of any type, Set objects are collections of values.
		A value in the Set may only occur once; it is unique in the Set's collection. 
		The Set has method checks if a value is in a Set object.
		

****- Array methods ?
Ans- Push() - Add one or more element to the end of an  array and return the new length of the array.
	
	UnShift()- Push and unshift both are same, but in the push() add element to the end and unshift() add element to start 
			in the array.
			
	Pop() - Removes the last element from an array.
	
	Shift() - Removes the starting element from an array.
	
	Splice()- 
	
	flat() - The flat() method creates a new array with all sub-array elements concatenated into
				it recursively up to the specified depth.  Flat() methos it is used for multiple inside array converted 
				into single array. [[[]]] => [][][] like.
				
	indexOf() - The indexOf() method returns the first index at which a given element can be found in the array, 
				or -1 if it is not present.
				ex- const beasts = ['ant', 'bison', 'camel', 'duck', 'bison'];

						console.log(beasts.indexOf('bison'));
						// Expected output: 1

						// Start from index 2
						console.log(beasts.indexOf('bison', 2));
						// Expected output: 4

						console.log(beasts.indexOf('giraffe'));
						// Expected output: -1

	
	
***- What is CSR(Client Side Rendering) and SSR(serevr Side Rendering)??

Ans- The main difference is that for SSR- your server’s response to the browser is the HTML of your
		page that is ready to be rendered,
	  CSR the browser will start rendering the HTML from your server without having to wait for all the JavaScript to be
		downloaded and executed. 
		
		In both cases, React will need to be downloaded and go through the same process of building a virtual dom 
		and attaching events to make the page interactive — but for SSR, the user can start viewing the page while all 
		of that is happening. 
		For the CSR world, you need to wait for all of the above to happen and then have the virtual dom moved to 
		the browser dom for the page to be viewable.
		
		We used the popular Next.js library for the SSR solution and the Create React App (CRA) library for the CSR solution.
		
		

*********JWT - JSON Web Token ?
 
 Ans- A JSON web token(JWT) is JSON Object which is used to securely transfer information over the web(between two parties). 
	 It can be used for an authentication system and can also be used for information exchange.
	 The token is mainly composed of header, payload, signature. These three parts are separated by dots(.).
	 
	 JWT defines the structure of information we are sending from one party to the another, and it comes in two forms
	 – Serialized, Deserialized.
	 The Serialized approach is mainly used to transfer the data through the network with each request and response. 
	 While the deserialized approach is used to read and write data to the web token.
	 
	 **Deserialized

	JWT in the deserialized form contains only the header and the payload.Both of them are plain JSON objects.

	** Serialized
JWT in the serialized form represents a string . all these three components make up the serialized JWT [header.payload.signature]. 
			
			
************** JS Questions ********************



1. Given an integer array nums of unique elements, return all possible subsets. The solution set must not contain duplicate subsets. Return the solution in any order.
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]

2. You are given a string s. You can convert s to a palindrome by adding characters in front of it.
Return the shortest palindrome you can find by performing this transformation.
Input: s = "aacecaaa"
Output: "aaacecaaa"

3. Given a string s that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.
Return a list of unique strings that are valid with the minimum number of removals. You may return the answer in any order.
Input: s = "()())()"
Output: ["(())()","()()()"]

4. Given an integer n, return the least number of perfect square numbers that sum to n.
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
SECTION 2 (Solve any 2)

1.  Create a React Component which passes 2 props namely rows(number) and columns(number) to a Child Component and Child Component renders a grid of div with some background colour with the same rows and columns as received from props.


2. Given an array of objects as following:
   const arr = [{id: 'AB',sum: 100,},
  {id: 'BC',sum: 200,},
  {id: 'CA',sum: 200,},
  {id: 'BC',sum: 500,},
  {id: 'AB',sum: 900,}];
Convert this array such that objects with same ids have one object and sum should be equal to sum of all objects of same id
[{id: 'AB',sum: 1000,},
  {id: 'BC',sum: 700,},
  {id: 'CA',sum: 200,}];
  
  
  3. Build a timer application using React JS. Users should be able to set a timer for a specified amount of time and receive alerts when the timer expires.


***QUE 1-  What is CLI?

Ans- React Native ships with its own build tool known as React Native Command Line Interface(CLI).
React Native is distributed as two npm packages, react-native-cli and react-native. 

In react native it is 2 CLI - Expo cLI and  React native CLI (Common Line Interface)


EXPO CLI - sudo npm i -g expo-cli     -install expo globally

then download the Expo app in ur mobile.
then install some extension - 1- react native tool debugging nd integrating
			      2- react native code snippet
			      3- prettier- code format
			      4- material icon -theme
			      
  expo init projectname  - creating project
  
  
  download xcode-  includes everything developers need to create great applications for Mac, iPhone, iPad, Apple TV, and Apple Watch. Xcode provides       developers                  a unified workflow for user interface design, coding, testing, and debugging.
  
  for debugging - ctrl + D nd command D.
  
  

***QUE 2- What are the key differences between React Native and ReactJS?

Ans- 
		**Usage Scope
    ReactJs - React is a  JavaScript library for building Responsive User Interfaces for Building Web Application.
    React Native - It is a framework for creating mobile applications with a native feel.
		**Syntax
    Both React and React Native uses JSX (JavaScript XML)  syntax but React uses html tags like <div> <h1> <p> etc while React Native uses <view> <text> etc.
     Animation And Gestures
    React uses CSS animations on a major scale to achieve animations for a web page while  The recommended way to animate a component is to use the Animated API provided      by React-Native.
 		**Routing Mechanism
    React uses a react-router for routing and does not have any inbuilt routing capabilities but React Native has a built-in Navigator library for navigating mobile a         		applications.

  
  
  			REACT JS 											REACT NATIVE
	It is used for developing web applications. 						It is used for developing mobile applications.
	It uses React-router for navigating web pages. 						It has a built-in navigator library for navigating mobile applications.
	It uses HTML tags. 									It does not use HTML tags.
	It provides high security. 								It provides low security in comparison to ReactJS.
	In this, the virtual DOM renders the browser code. 					In this, Native uses its API to render code for mobile applications.
  
  
  
  
 ***QUE-  What is Flexbox and describe any elaborate on its most used properties?
 
 Ans- It is a layout model that allows elements to align and distribute space within a container. With Flexbox when Using flexible widths and heights, 
	 all the inside the main container can be aligned to fill a space or distribute space between elements, 
 	which makes it a great tool to use for responsive design systems.
 	
	  Property  		        Values 										Description
	  
	flexDirection 		‘column’,'row' 							   Used to specify if elements will be aligned vertically or horizontally 
	justifyContent 		‘center’,'flex-start','flex-end','space-around','space-between'    Used to determine how should elements be distributed inside the container 
	alignItems 		‘center’,'flex-start','flex-end','stretched' 			   Used to determine how should elements be distributed inside the container ,								
													along the secondary axis (opposite of flexDirection) 
	
	
	
***QUE- Describe advantages of using React Native?

Ans-  React Native runs multiple processes. 3 main processes run in React Native and 1 process that only runs on Android L (5.0).
        If you want to create more processes, you can also use the library react-native-threads.
        The React Native renderer distributes the work of the render pipeline across multiple threads.

    UI Thread.        -            This process is used for handling rendering android and ios views.
    JS Thread.        -             This process is used for handling all of the logic of your react native application.
    React Native Modules Thread. -  This happens when an app needs to access a platform API. For example, if you’re working with animations, you may use the native driver 
                                           to handle your animations.
    React Native Render Thread. -    Android L (5.0) only uses this to draw the UI with OpenGL. Because this is only used in specific situations, I will ignore this process 
                                        moving forward and only write about the main 3.	
	
	

***Que-Are default props available in React Native and if yes for what are they used and how are they used ?

Ans-Yes, default props available in React Native as they are for React,  If for an instance we do not pass props value, the component will use the default props value.

eg- 	import React, {Component} from 'react';
	import {View, Text} from 'react-native';
	class DefaultPropComponent extends Component {
	   render() {
	       return ( 
		   <View>
		     <Text> 
		      {this.props.name} 
		    </Text> 
		  </View>
	       )
	   }
	}
	Demo.defaultProps = {
	   name: 'BOB'
	}

	export default DefaultPropComponent;
	
	
	
	
***QUE- What is State and how is it used in React Native?

Ans-  It is used to control the components. The variable data can be stored in the state. It is mutable means a state can change the value at any time.

	import React, {Component} from 'react';    
	import { Text, View } from 'react-native';    
	export default class App extends Component {    
	 state = { 
	myState: 'State of Text Component'
		      }
	updateState = () => this.setState({myState: 'The state is updated'})
	render() {
	return (
	<View>    
	<Text onPress={this.updateState}> {this.state.myState} </Text>    
	</View> 
	); } }

   Here we create a Text component with state data. The content of the Text component will be updated whenever we click on it. The state is updated by event onPress .


  	
 
 ***QUE-  Describe Timers in React Native Application ?

Timers are an important and integral part of any application and React Native implements the browser timers.

Timers - setTimeout, clearTimeout
	  setInterval, clearInterval
	  setImmediate, clearImmediate
	  requestAnimationFrame, cancelAnimationFrame
	  
	  
	  
***QUE- How to debug React Native Applications and Name the Tools used for it ?

Ans- In the React Native world, debugging may be done in different ways and with different tools, since React Native is composed 
	of different environments (iOS and Android), which means there’s an assortment of problems and a variety of tools needed for debugging. 
	
	The Developer Menu:

		Reload: reloads the app
		Debug JS Remotely: opens a channel to a JavaScript debugger
		Enable Live Reload: makes the app reload automatically on clicking Save
		Enable Hot Reloading: watches for changes accrued in a changed file
		Toggle Inspector: toggles an inspector interface, which allows us to inspect any UI element on the screen and its properties, 
					 and presents an interface that has other tabs like networking, which shows us the HTTP calls, and a tab for performance.	
					
					
	Chrome’s DevTools:
	
	React Developer Tools:
		For Debugging React Native using React’s Developer Tools, you need to use the desktop app. In can installed it globally or locally in your project by just 
		       running the following command:
		yarn add react-devtools
		Or npm:
		npm install react-devtools --save

		React’s Developer Tools may be the best tool for debugging React Native for these two reasons:
		It allows for debugging React components.
		There is also a possibility to debug styles in React Native. There is also a new version that comes with this feature that also works with the inspector in 
		     the developer menu.
		     
	React Native Debugger:      react Native CLI

		You can use the React Native CLI to do some debugging as well. It can also be used for showing the logs of the app. Hitting react-native log-android will 
		    show you the logs of db logcat on Android, and to view the logs in iOS you can run react-native log-ios, and with console.log you can dispatch logs to 
		     the terminal:

		console.log("some error🛑")
		
		
		
		
***QUE- Describing Networking in React Native and how to make AJAX network calls in React Native?

Ans- React Native provides the Fetch API for networking needs. 
	To fetch content from an arbitrary URL, we can pass the URL to fetch:
		fetch('https://mywebsite.com/endpoint/', {
		 method: 'POST',
		 headers: {
		   Accept: 'application/json',
		   'Content-Type': 'application/json'
		 },
		 body: JSON.stringify({
		   firstParam: 'yourValue',
		   secondParam: 'yourOtherValue'
		 })
		});
  
   Networking is an inherently asynchronous operation. Fetch methods will return a Promise that makes it straightforward to  
   	write code that works in an asynchronous manner:

		const getMoviesFromApi = () => {
		 return fetch('https://reactnative.dev/movies.json')
		   .then((response) => response.json())
		   .then((json) => {
		     return json.movies;
		   })
		   .catch((error) => {
		     console.error(error);
		   });
		};
  
  The XMLHttpRequest API is built in to React Native  Since frisbee and Axios use XMLHttpRequest we can even use these libraries.
  
  
  
  
***QUE- What is a bridge and why is it used in React Native ? Explain for both android and IOS ?

ANS- Bridge in ReactNative is a layer.
	The layer which is closest to the device on which the application runs is the Native Layer.
 
	The bridge is basically a transport layer which acts as a connection between Javascript and Native modules, it does the work of 
	transporting asynchronous serialized batched response messages from JavaScript to Native modules.
	 
	 
	 
***QUE- What is fabric?
Ans- 
	 
	 
***QUE-  Name core Components in React Native and the analogy of those components when compared with the web .

Ans- The core components used in React Native are <View> , <Text> , <Image> , <ScrollView> , <TextInput>

 		REACT NATIVE UI COMPONENT 	                   ANDROID VIEW 	         IOS VIEW 	               WEB ANALOG 	
			<View> 						<ViewGroup> ole of JSX in React Nole of JSX in React N		<UIView> 		A non-scrolling <div> 	
			<Text> 						<TextView> 		<UITextView> 			<p> 	
			<Image> 					<ImageView> 		<UIImageView> 			<img> 	
			<ScrollView> 					<ScrollView> 		<UIScrollView> 			<div> 	
			<TextInput> 					<EditText> 		<UITextField> 			<input type="text">
			
			

***QUE- What is ListView and describe its use in React Native ?

Ans- React Native ListView is a view component that contains the list of items and displays it in a vertically scrollable list.



***QUE- How can you write different code for IOS and Android in the same code base ? Is there any module available for this ?

ANS-  The platform module detects the platform in which the app is running.

	import { Platform, Stylesheet } from 'react-native';
	const styles = Stylesheet.create({
	height: Platform.OS === 'IOS' ? 200 : 400
	})

 Additionally Platform.select method available that takes an object containing Platform.OS as keys and returns the value for the platform you are currently on.



***QUE-  What are Touchable components in react Native and which one to use when ?

Ans-  Tapping gestures can be captured by Touchable components and can display feedback when a gesture is recognized.

	Depending on what kind of feedback you want to provide we choose Touchable Components.

	Generally, we use TouchableHighlight anywhere you would use a button or link on the web. The background of the view will be darkened when the user presses down on 
		the button.

	We can use TouchableNativeFeedback on Android to display ink surface reaction ripples that respond to the user's touch.

	TouchableOpacity can be used to provide feedback by reducing the opacity of the button, allowing the background to be seen through while the user is pressing down.

	If we need to handle a tap gesture but you don't want any feedback to be displayed, use TouchableWithoutFeedback.




***QUE- Explain FlatList components, what are its key features along with a code sample ?

Ans-  The FlatList component displays similarly structured data in a scrollable list. It works well for large lists of data where
	 the number of list items might change over time.

	Key Feature:  The FlatList shows only those rendered elements which are currently displaying on the screen, not all the elements of the list at once.





***QUE- 21. How To Use Routing with React Navigation in React Native ?

Ans-   One of the popular libraries for routing and navigation in a React Native application is React Navigation.

	This library helps solve the problem of navigating between multiple screens and sharing data between them.



***QUE-  What are the Different Ways to style React Native Application ?

Ans- React Native give us two powerful ways by default to style our application :

1 ) Style props- 

	import React, {Component} from 'react';
	import {Platform, StyleSheet, Text, View} from 'react-native';
	export default class App extends Component<Props> {
	render() {
	return (
	<View style={{flex:1,justifyContent:"center",backgroundColor:"#fff", alignItems:"center"}}>
	<View style={{width:200,height:150,backgroundColor:"red",padding:10}}>
	<Text style={{fontSize:20, color:"#666"}}>Styled with style props</Text>
	</View>
	</View>
	);
	}
	}

2 ) Using StyleSheet-
3 )  styled-components in React Native


***QUE-  Explain Async Storage in React Native and also define when to use it and when to not?

    Async Storage is the React Native equivalent of Local Storage from the web.
    Async Storage is a community-maintained module for React Native that provides an asynchronous, unencrypted, key-value store. Async Storage is not shared between apps: 
          every app has its own sandbox environment and has no access to data from other apps.

        		DO USE ASYNC STORAGE WHEN..                                                         DON'T USE ASYNC STORAGE FOR..
		Persisting non-sensitive data across app runs 							Token storage
		Persisting Redux state 										Secrets
		Persisting GraphQL state 	 
		Storing global app-wide variables




***QUE-  What’s the real cause behind performance issues in React Native ?

Ans-   The real cause behind React Native performance issues is that each thread (i.e Native and JS thread) is blazingly fast. The performance bottleneck in React Native app occurs 
when you’re passing the components from one thread to another unnecessarily or more than required. A major thumb rule to avoid any kind of performance-related issue in React 
Native is to keep the passes over the bridge to a minimum. 

    Native thread built for running Java/ Kotlin, Swift/ Objective C
    Javascript thread is the primary thread that runs everything from javascript-based animations to other UI components
    The bridge as the name suggests acts as an  intermediate communication point for the native and JS thread

 


***QUE-  List down some of the steps to optimize the application.

	 AnS- -Use Proguard to minimize the application size.
	      -Create reduced-sized APK files for specific CPU architectures. When you do that, your app users will automatically get the relevant APK file for their 
	 	 specific phone’s architecture. 
 	      -Compress images and other graphic elements. Another option to reduce image size is using file types like APNG in place of PNG files.
	      -Don’t store raw JSON data,  eIther we need to Compress it or convert it into static object IDs.
	    -  Optimize native libraries.
	     - Optimize the number of state operations and remember to use pure and memoized components when needed
	    - Use Global State wisely for example worst-case scenario is when state change of single control like TextInput or CheckBox 
	       propagates render of the whole application. Use libraries like Redux or Overmind.js to handle your state management in a more optimized way.
	    - Use key attribute on list items, it helps React Native to pick which list to update when rendering a long list of data 
	    - Use VirtualizedList, FlatList, and SectionList for large data sets.
	    - Clear all the active timers which may lead to heavy memory leakage issues.


 	

***QUE- Describe Memory leak Issue in React Native , how can it be detected and resolved ?

Ans-  graph of allocated objects and their references. If it happens to encounter a part of the graph that is not being referenced directly or indirectly from root objects 
	(e.g., variables on the stack or a global object like window or navigator) that whole part can be deallocated from the memory.

    In React Native world each JS module scope is attached to a root object. Many modules, including React Native core ones, declare variables that are kept in the main 
	scope (e.g., when you define an object outside of a class or function in your JS module). Such variables may retain other objects and hence prevent them from being 
	garbage collected.
	
	

***QUE -  Is there any out of the box way storing sensitive data in React ? If yes which and if not how can this be achieved ?

Ans-	React Native does not come bundled with any way of storing sensitive data. However, there are pre-existing solutions for Android and iOS platforms.

	iOS - Keychain Services
	Keychain Services allows you to securely store small chunks of sensitive info for the user. This is an ideal place to store certificates, tokens, passwords, and any 
	  other sensitive information that doesn’t belong in Async Storage.

	Android - Secure Shared Preferences#
	Shared Preferences is the Android equivalent for a persistent key-value data store. Data in Shared Preferences is not encrypted by default, but Encrypted Shared 
	Preferences wraps the Shared Preferences class for Android, and automatically encrypts keys and values.

	Android - Keystore
	The Android Keystore system lets you store cryptographic keys in a container to make it more difficult to extract from the device. In order to use iOS Keychain 
	services or Android Secure Shared Preferences, you can either write a bridge yourself or use a library that wraps them for you and provides a unified API at your own 
	risk. Some libraries to consider:

	    Expo-secure-store
	    React-native-keychain
	    react-native-sensitive-info - secure for iOS, but uses Android Shared Preferences for Android (which is not secure by default). There is however a branch that 
	    uses Android Keystore.


 	
 	
***QUE- What is Network Security and SSL Pinning?
Ans-




***QUE- Explain setNativeProps. Does it create Performance issues and how is it used ?
Ans-




***QUE- How to make your React Native app feel smooth on animations ?
Ans- 



 	
***QUE- How to make .apk file in react native?
Ans-  An Android Package Kit (APK) is the package file format used by the Android OS for distribution and installation of mobile apps.
	 It is similar to the .exe file you have on Windows OS, a .apk file is for android. 	
	 The application package files in iOS are called .ipa files. IPA stands for "iOS App Store Package". 





***QUE- What is meant by InteractionManager, and why it is Important?
Ans-  InteractionManager allows long-running work to be scheduled after any interactions/animations have completed. In particular, this allows JavaScript animations to run smoothly.

	Applications can schedule tasks to run after interactions with the following:

	InteractionManager.runAfterInteractions(() => {
	  // ...long-running synchronous task...
	});

	Compare this to other scheduling alternatives:

	    requestAnimationFrame(): for code that animates a view over time.
	    setImmediate/setTimeout(): run code later, note this may delay animations.
	    runAfterInteractions(): run code later, without delaying active animations.
	 	
 	Methods
		**runAfterInteractions()

		-static runAfterInteractions(task?: (() => any) | SimpleTask | PromiseTask);
		Schedule a function to run after all interactions have completed. Returns a cancellable "promise".
		
		**createInteractionHandle()

		-static createInteractionHandle(): Handle;
		Notify manager that an interaction has started.
		
		**clearInteractionHandle()

		-static clearInteractionHandle(handle: Handle);
		Notify manager that an interaction has completed.
		
		**setDeadline()

		-static setDeadline(deadline: number);
		A positive number will use setTimeout to schedule any tasks after the eventLoopRunningTime hits the deadline value, otherwise all 
		tasks will be executed in one setImmediate batch (default).

 	
 	
 QUE- What are animations in React Native?

Ans-   The animation is a method in which images are manipulated to appear as moving objects. React Native animations allows you to add extra effects, which provide great 
	user experience in the app. We can use it with React Native API, Animated.parallel, Animated.decay, and Animated.stagger.

	React Native has two types of animation, which are given below-

    Animated: This API is used to control specific values. It has a start and stops methods for controlling the time-based animation execution.
    LayoutAnimated: This API is used to animate the global layout transactions.

 	
 	
 	
*** QUE- How React Native handle different screen sizes?

Ans-  React Native provides many ways to handle screen sizes. Some of them are given below:

1. Flexbox: It is used to provide a consistent layout on different screen sizes. It has three main properties:

    flexDirection
    justifyContent
    alignItems

2. Pixel Ratio: It is used to get access to the device pixel density by using the PixelRatio class. We will get a higher resolution image if we are on a high pixel density 
   device.

3. Dimensions: It is used to handle different screen sizes and style the page precisely. It needs to write the code only once for working on any device.

4. AspectRatio: It is used to set the height or vice versa. The aspectRatio is present only in React-Native, not a CSS standard.

5. ScrollView: It is a scrolling container which contains multiple components and view. The scrollable items can be scroll both vertically and horizontally.
	
 	
 	
 ***QUE-How is data loaded on the server by React Native?

Ans- React Native uses Fetch API to fetched data for networking needs.


***QUE- What is meant by Gesture Responder System?

Ans-   It is an internal system of React Native, which is responsible for managing the lifecycle of gestures in the system. React Native provides several 
	different types of gestures to the users, such as tapping, sliding, swiping, and zooming. The responder system negotiates these touch interactions. 
	Usually, it is used with Animated API. Also, it is advised that they never create irreversible gestures.
	 	
 	
 	
 ***QUE- How do you manage state in React Native?	
 Ans-  There are four main types of state you need to properly manage in your React apps:

    Local state
    Global state
    Server state
    URL state
    
    Local (UI) state – Local state is data we manage in one or another component.Local state is most often managed in React using the useState hook.	
 			useReducer is another option that can be used for either local or global state.
 			The benefit of useReducer is that it provides a built-in way to perform a number of different state operations with the help of the reducer function, 
 			which makes it more dynamic overall than useState.
 	
  Global State-  You will reach a point in your application where patterns like “lifting state up” and passing callbacks down to 
   update your state from components lead to lots and lots of props.
 	 Many developers are inclined to use built-in React features like the Context API to manage their state.
    To be clear: the Context API is not a state management solution. It is a way to avoid problems like props drilling
     (creating a bunch of props in components that don’t need it), but it is only helpful for reading state, not updating it.
 	
  Server State- At first, it seems you just need to fetch data and display it in the page. But then you need to display a loading 
  	spinner while you are waiting for the data. Then you need to handle errors and display them to the user as they arise.	
    To fix this, there are a couple of great libraries that make data fetching in React a breeze: SWR and React Query.
    useSWR react hooks for data fetching.
    They not only give us a convenient hook to both get and change data from an API, but they keep track of all the necessary states and cache the data for us.
	eg -             import useSWR from 'swr';
			const fetcher = url => fetch(url).then(r => r.json())

			function User() {
			  const { data, error } = useSWR('/api/user', fetcher)

			  if (error) return <div>failed to load</div>
			  if (!data) return <div>loading...</div>
			  
			  return <div>hello {data.name}!</div>
			}
	
   URL State-  If you are using React Router, you can get all the information you need using useHistory or useLocation.
 			if you have any route parameters that you need to use, for example to fetch data based off of, you can use the useParams hook.
 			f you are using Next.js, almost everything can access directly from calling useRouter.
 			
 			
 
 ***QUE- How do you optimize performance in React Native?
 Ans- 1. Reduce Unnecessary Re-Renders With useMemo Hook -  React Native renders components using a Virtual DOM (VDOM) technology.
 			The React library provides the useMemo and useCallback hooks to solve this problem in functional components. You can use 
 			the useMemo hook to memoize the resulting value of a JavaScript function that you don't want to recompute on every render.
 	
     2. Effective State Data Handling  -  Poor state management can lead to data inconsistencies, leading to unexpected behavior that 
     			can be difficult to track down and fix.
		 Good state management involves avoiding storing unnecessary data in the state, which can slow down the app and make it harder to debug.
		  It is important to ensure that all state you store is absolutely necessary for the component to render.
		   Another way to update state effectively is to use immutability techniques, like the spread operator or the Object.assign() method.
	 	
    3.  Implement a Performance Monitoring System  -  Mobile app performance monitoring systems (PMS) are tools that let you measure and analyze 
    			the performance of your mobile apps. They provide features such as real-time monitoring, crash reporting, 
    			network monitoring, performance metrics, and user session replay.	
 	
   4. Remove Console.log Statements  - When a console.log statement runs, it sends a message to the JavaScript engine to log the message to the console. 
   		The JS engine then takes time to process and display the message.
		Too many console statements in your code will slow down its execution and cause performance delays. 
		This can be especially problematic when your app runs on a device with limited resources, such as a low-end mobile device.	
 	
   5.Build an Efficient Navigation System -   A good navigation system will improve the overall structure of your React Native app, making it 
     		easier to maintain, update features, and pass state data around efficiently. Additionally, it makes switching between
     		 multiple displays in your application much easier, improving the user experience.
     		 You should consider factors like the right navigation pattern (tab-based, stack-based, drawer-based, etc.) to suit your app. 
     		 
    6.Reduce App Size With Code Splitting and Lazy Loading - App size is important for optimized performance because it can affect aspects 
    			of the user experience, like initial load time, memory usage, and storage space.
		Code splitting and lazy loading are techniques that can reduce your React Native app’s size and improve performance.
 	
 	
 ***QUE- What is the role of JSX in React Native?
 Ans- React and React Native use JSX, a syntax that lets you write elements inside JavaScript like so: <Text>Hello, I am your cat!</Text>.
      
      
 
 ***QUE-  How do you implement navigation in a React Native app?      
 Ans- React Navigation is a standalone library that enables you to implement navigation functionality in a React Native application.	
 	
 	
 	
 ***QUE- What is the role of AsyncStorage in React Native?
 Ans- AsyncStorage is React Native’s API for storing data persistently over the device. It’s a storage system that developers can use and save 
 	data in the form of key-value pairs. 	
 	AsyncStorage API is asynchronous, so each of its methods returns a Promise object and in case of error, an Error object. 
 	AsyncStorage can prove very helpful when we want to save data that the application would need to use, even when the user has closed it or has even closed the device.
 	
 	eg-                  Let’s set a new key called userId along with its value:

		const userId = '8ba790f3-5acd-4a08-bc6a-97a36c124f29';const saveUserId = async userId => {
		  try {
		    await AsyncStorage.setItem('userId', userId);
		  } catch (error) {
		    // Error retrieving data
		    console.log(error.message);
		  }
		};


***QUE- How do you handle network requests in React Native?

Ans- by using fetch nd axios pkg		 	
 	
 	
 	
 
 ***QUE-  How do you handle device-specific features such as camera and location in React Native?
 ANS- Installing Dependencies - npx react-native init qrCodeScannerApp
 				cd qrCodeScannerApp
 			
 			yarn add react-native-camera
 			
 			
 		eg-     import React, { Component } from 'react'
			import { StyleSheet, View, Alert } from 'react-native'
			import { RNCamera } from 'react-native-camera'

			class App extends Component {
			  render() {
			    return (
			      <View style={styles.container}>
				<RNCamera
				  style={{ flex: 1, alignItems: 'center' }}
				  ref={ref => {
				    this.camera = ref
				  }}
				/>
			      </View>
			    )
			  }
			}
			const styles = StyleSheet.create({
			  container: {
			    flex: 1,
			    flexDirection: 'column',
			    backgroundColor: 'black'
			  }
			})

			export default App;
			

 ***QUE-  How do you handle errors in React Native?
 Ans-React comes with a solution for error handling in the form of error boundaries. However, as the documentation tells us, 
 	these boundaries are of no use for code that crashes in event handlers. They’re only useful for errors that appear during rendering.
 	
 	
 
 ***QUE- What is the difference between Android and iOS development in React Native?	
 Ans- React Native utilizes JavaScript codebase for multiple platforms. It also allows for sharing and reusing most 
	 of the code between iOS and Android. By reusing the same code, you not only speed up the development process, 
	 but also require less resources: there is no need for separate iOS and Android teams.	
 	
 	iOS -  Xcode ,Mac OS ,CocoaPods
 	Android - Java Development Kit, Android Studio,  Android SDK and related configuration
 	
 	
	Release Process - android - play store
			  IOs-   app store
 	
 	
 ***QUE- What is the purpose of a bridge module in React Native?	
 Ans- The React Native Bridge allows the native code and the javascript code to talk to each other. Without the bridge, 
 	there is no way for the native code to send any information to the JavaScript code	
     You tap your app icon to open your app and the OS creates a Main Thread(aka a UI thread) and assigns it to your app. 
      The main thread spawns the JavaScript thread and the shadow thread.	
 	
 	React Native allows developers to create their own module(s) in Native Code (Objective-C & Java for MQ purposes). 
 	It allows developers to bridge these modules into the project so that the top-level JavaScript layer can interact with 
 	those modules and use them within that JS layer.
 	
 	
 	
 ***QUE- How do you implement internationalization (i18n) in React Native?
 Ans- “i18n” is the abbreviation for Internationalization . I18n is the process of developing a software so that it can handle local languages and cultural settings. 
        npm install react-i18next i18next --save

  Configure i18next

 create a new folder named “localization” inside src. Also,Create a new file “i18n.ts” containing follwing content.

eg-		import i18n from 'i18next';
		import { initReactI18next } from 'react-i18next';
		import en from './en';
		import fr from './fr';
		import gu from './gu';const resources = { // list of languages
		 en,
		 fr,
		 gu,
		};i18n.use(initReactI18next) // passes i18n down to react-i18next
		 .init({
		  compatibilityJSON: 'v3', //To make it work for Android devices, add this line.
		  resources,
		  lng: 'en', // default language to use.
		  // if you're using a language detector, do not define the lng optioninterpolation: {
		   escapeValue: false,
		  },
		 });export default i18n;
		 
 
 
 	
 	
 ***QUE- How do you handle push notifications in React Native?
 Ans- 
 
 
 	
 
 
 
 ***QUE-  How do you handle layout changes in React Native?
 Ans-
 
 
 
 
 	
 	
 	
 	
 	
 	

    What are the benefits of using React Native?
    How does React Native differ from React?
    How do you manage state in React Native?
    What is the difference between props and state in React Native?
    What are the key components of React Native?
    How do you optimize performance in React Native?
    How do you handle user input in React Native?
    What are some common lifecycle methods in React Native?
    What is Redux and how does it work with React Native?
    What is the role of JSX in React Native?
    How do you implement navigation in a React Native app?
    What is the role of AsyncStorage in React Native?
    How do you handle network requests in React Native?
    How do you handle device-specific features such as camera and location in React Native?
    How do you handle errors in React Native?
    What is the difference between Android and iOS development in React Native?
    What is the purpose of a bridge module in React Native?
    How do you handle styling in React Native?
    What is the role of Flexbox in React Native?
    How do you implement animations in React Native?
    How do you implement internationalization (i18n) in React Native?
    How do you test React Native applications?
    What are some common debugging techniques in React Native?
    How do you handle push notifications in React Native?
    What is the difference between a functional component and a class component in React Native?
    How do you handle touch events in React Native?
    How do you handle layout changes in React Native?
    How do you handle offline support in React Native?
    How do you integrate third-party libraries in React Native?
    How do you handle deep linking in React Native?
    How do you handle text input in React Native?
    What is the role of FlatList and SectionList in React Native?
    How do you handle image loading in React Native?
    How do you handle gestures in React Native?
    How do you handle accessibility in React Native?
    How do you handle permissions in React Native?
    How do you implement a custom font in React Native?
    How do you handle device orientation in React Native?
    How do you handle background tasks in React Native?
    How do you handle app updates in React Native?
    What is the difference between a controlled and uncontrolled component in React Native?
    How do you handle user authentication in React Native?
    How do you handle data persistence in React Native?
    How do you handle data synchronization in React Native?
    What are some common security issues in React Native?
    How do you implement a splash screen in React Native?
    How do you implement a side menu in React Native?
    What is the difference between React Native and Ionic?
    How do you handle responsive design in React Native?
    What is the role of Expo in React Native?

event loop
callback
higher order function
 ts vs js
angular js vs angular
pipe and types of pipe
directive
routing
component to component commmunication
guard
websocket and poling
constructor vs onInit
 lifecycle hooks
 DI and services
 new feature of angular
 observalble and subject vs behavioual subject
Code ----
1.write a promise to check prime number?
2.async function foo() {​​ const result1 = await new Promise((resolve) =>   setTimeout(() => resolve("1")), ); const result2 = await new Promise((resolve) =>   setTimeout(() => resolve("2")), ); }​​ foo(); (edited) 

**********************************************
let a = { name: 'john' };
    let b = a;
    b.name = 'deo';
    console.log(a);
    console.log(b);
1. What is the output of code.
2. Why the value of a and b are same?
3. If we want to change the output then what changes need to do.
2. What is the output of the following code and why?
console.log(1);
setTimeout(() => console.log(2), 0);
console.log(3);
3. What is closure and its use and example.
4. What is the spread operator.
5. How can spread array and object.
6. Why we can use the spread operator.
7. What is authentication.
8. Which authentication is used to secure your APIs.
9. Why password is not added to the JWT token?
10. What are promises.
    1. If we want to call two APIs and send a response after completing both the APIs. How can we achieve it?
     2. If one of API call gets failed and we want to send both result to client then what method would be used?
11.  user collection:
[
  {name: "person a", skills: ['mysql', 'mongo', 'react'] },
  {name: "person b", skills: ['node', 'mongo', 'react'] },
...
]
1. Write a query to get all the user details with matching skills 'react' or 'mongo'
2. Write a query to get all the user details with matching skills 'react' and 'mongo'
1. Difference  between let, var, and const
2. Which promise method is used to execute all API calls parallel
3. What is the bind method and the difference between call and bind.
4. What will be the output of the following code and why?
function two() {
    console.log('myVar', myVar);
}
function one() {
    var myVar=2
    two()
}
var myVar=1
one()
5. What will be the output of the following code and why?
function printHello() {
    console.log('Hello')
}
printHello()
6. What will be the output of the following code and why?
printHello2()
var printHello2 = function() {
    console.log(' printHello2 Hello')
}
7. What is an event loop?
8. What will be the output of the following code and why?
console.log('Log first')
setTimeout(function(){console.log('Log second')},3000)
setTimeout(function(){console.log('Log third')},0)
console.log('Log fourth')
9. What is sharding in MongoDB?
10. Why MongoDB is better than SQL database?
11. What are the operators available in MongoDB?
12. What is unwind?
13. Find the second highest salary from the table
14. Find all the users having a role developer whose age is less than 27.
15.  What are authentication and authorization?
16.  Which authentication module is used in your project.
17.  Where you are storing the JWT token?
18. How do you manage expired JWT tokens?
19. After the token expires are you logging out the user from the app?
20. What is the other way to manage expired tokens so that users don't need to do logout and login again?

Last round of interview Asked about the following topics
Past projects
API standards
Security standards
Scaling Application
Managing multi-role functionality
Code review standards

*************************************************
what are the mongoose operators you have used
$skip
$size
2 what is closure?
3 how will you achieve api versioning?
4 functions used in unit testing
5 which Promise functions you have used like Promise.all()
6 advantages of nosql over sql
7 what is cluster in node js
[6:03 PM] output of following programs

for(var i=0;i<100;i++){
  setTimeout(()=>{console.log(i)},0)
}
let obj={foo:"bar"};
let obj1=obj;
obj1.foo=6;
console.log(obj1.foo)
console.log(obj.foo)

return toppers data from students table using mongoose query
js is synchronous or asynchronous ?
does javascript use oop?
[6:10 PM] what is $lookup in aggregation?
[6:14 PM] output for following prog
let number=0
console.log(number++)
console.log(++number)
console.log(number)

what is the difference between var and let?
what is the difference between arrow fun  and normal function?





async function asyncDemo(x,y){
   let promise = new Promise((resolve,reject)=>{
       setTimeout(()=>resolve("Output: "+(x+y)),5000);
       setTimeout(()=>resolve("Output: "+(x-y)),3000);
   });
   console.log(x+y);
   let result = await promise;
   console.log(result);
}
asyncDemo(20,15);


console.log('a')
setTimeout(()=>{
    console.log("b")
    setTimeout(function() {
        console.log("c")
    }, 1000);
},3000)
console.log("d")
setTimeout(()=>{
    console.log('e')
},0)
setTimeout(()=>{
    console.log('f')
},5000)



function a(x){
  var x = 10
 function b(){
    x++
    console.log(x)
    var x = 20
  }
  b()
}
a(5)


Promise and observable
Loading and its type
JWT Interceptor
Diff betwn Bearer token and Access token
Reactive form and Directive form in angular
Life cycle methods
What is generated when we do ng new <project name>
Have you created custom directive
How can i call a button dynamically depending upon whether it has a id property of not
(if it have an id call save() if it do not call update())

Js Questions
every, sum and includes() in js
How will you show nested array values in html

Css Questions
What is mixing in saas
What is pseudo class and pseudo elements
Flex box and flex grid
Block and inline property
border-box and content-box

HTML 
Diff betwn html and html5
given= multi(1)(2)(3) you have to write multi function a code which will return 6
var arr=[10,2,4,9,20,30];
 console.log(arr.sort((a,b)=>a-b)[0])
 console.log(Math.min(...arr))
 difference between null and undefined?
type of undefined?
type of null?
Hoisting?
use strict?
promise vs observable?
what is lazy Observable?
 //output of code
console.log("start");
Promise = new Promise((resolve, reject) => {
    console.log(1);
    resolve(2);
    console.log(3);
})
Promise.then(response => {
    console.log(response);
});
console.log("end")
call,apply?
Explain differences and write example?
Injecter?
What is ViewEncapsulation?
Type of ViewEncapsulation explain each?
How to make Api request using observable write example?
 What is directive and its type?explain each type?
what is pipe and what are the  types?Explain each?
arr=[1,2,3,4];
10:02
delete arr[1];
10:03
arr.length;@here O/p please
What is Event bubbling.
What is diff betn RouterModule.forRoot() & RouterModule.forChild().
What is async and await
What is AJAX in vanila js
What is service workers
What is flex-box
How can we handle error in Observables?
What is scan() and reduce() operators in Observable?
What is diff betn Injectable and Injector?
<div data-val="1" /> what is data-val in given html element.
What is window.onload and document.ready
Difference between arrow function and normal function.
Js code
write a code to find the numbers which are repeated more then array.length/2 .  array=[1,2,1,3,1,2];
a=2;
b=a;
is it a shallw copy or deep copy?if it is shallow how to create deep?
what is priority of function in js;
str=cviic
check is palendrom or not?
if not the make it palendrom if posible?
obj = {
    "first" : "pahila",
    "second" : "dusra"
} write a code and  to make seprate array of keys
["first","second"]
let name="yash";
  let address="Baramati";
  
  obj1={
    name:name,
    address:address,
  }
  
  obj2={
    name,
    address,
  }
  
  console.log(obj1);
  console.log(obj2);
  console.log(abc())
console.log(temp)
function abc(){
    return "hello"
}
var temp=()=>{
   return "hello"
}

event loop
callback
higher order function
 ts vs js
angular js vs angular
pipe and types of pipe
directive
routing
component to component commmunication
guard
websocket and poling
constructor vs onInit
 lifecycle hooks
 DI and services
 new feature of angular
 observalble and subject vs behavioual subject
Code ----
1.write a promise to check prime number?
2.async function foo() {​​ const result1 = await new Promise((resolve) =>  setTimeout(() => resolve(“1”)), ); const result2 = await new Promise((resolve) =>  setTimeout(() => resolve(“2")), ); }​​ foo();

let number=0
console.log(number++)
console.log(++number)
console.log(number)
for(var i=0;i<100;i++){
  setTimeout(()=>{console.log(i)},0)
}
function two() {
    console.log('myVar', myVar);
}
function one() {
    var myVar=2
    two()
}
var myVar=1
one()
5. What will be the output of the following code and why?
var a = 10;
delete a;
console.log(a)
var b = 20;
console.log(delete b)
)what is the difference between hidden and ngIf
2)what is observable
3)what is pipe and tell its type
4)box model in css
5)difference between call and apply
6)what is directive and explain its type
7)explain server side rendering
8)shallow copy and deep copy
9)inline html in decorator
10)promise in js..
11)did you create custom pipe and which?
12)what is dependency injection..
13)how update request handle in node js and using which method
14)what is stream and how can you use in node js?
1.do you know what current angular vs angular js
2.did you create custom directive and tell its types also
3.what is pipe and its type and did you create any custom pipe
4.what is lazy loading and when it is load
5.how many ways we can communicate with the component
6.what is observable
7.difference between promise and observable
8.how can you improve the application performance
8.what is aot and jit
9.what is memory leaked problem
10.what is dependency injection
11.why we use promise
12.what is async and await
13.difference between typescript and javascript
14.code:
var prom = new Promise((resolve,reject)=>{
    setTimeout(()=>{
        resolve(10);
    },100*3);
})
prom.then((data)=>{
    console.log(data);
    return data*2;
}).then((data)=>{
    console.log(data);
    return data;
})
guess the output??
*after guessing can you apply async and await in below the code 
what are the mongoose operators you have used
$skip
$size
2 what is closure?
3 how will you achieve api versioning?
4 functions used in unit testing
5 which Promise functions you have used like Promise.all()
6 advantages of nosql over sql
7 what is cluster in node js
[6:03 PM] output of following programs
for(var i=0;i<100;i++){
  setTimeout(()=>{console.log(i)},0)
}
let obj={foo:"bar"};
let obj1=obj;
obj1.foo=6;
console.log(obj1.foo)
console.log(obj.foo)
return toppers data from students table using mongoose query
js is synchronous or asynchronous ?
does javascript use oop?
[6:10 PM] what is $lookup in aggregation?
[6:14 PM] output for following prog
let number=0
console.log(number++)
console.log(++number)
console.log(number)
what is the difference between var and let?
what is the difference between arrow fun  and normal function?
event loop
callback
higher order function
 ts vs js
angular js vs angular
pipe and types of pipe
directive
routing
component to component commmunication
guard
websocket and poling
constructor vs onInit
 lifecycle hooks
 DI and services
 new feature of angular
 observalble and subject vs behavioual subject
Code ----
1.write a promise to check prime number?
2.async function foo() {​​ const result1 = await new Promise((resolve) =>   setTimeout(() => resolve("1")), ); const result2 = await new Promise((resolve) =>   setTimeout(() => resolve("2")), ); }​​ foo(); (edited)
**********************************************
let a = { name: 'john' };
    let b = a;
    b.name = 'deo';
    console.log(a);
    console.log(b);
1. What is the output of code.
2. Why the value of a and b are same?
3. If we want to change the output then what changes need to do.
2. What is the output of the following code and why?
console.log(1);
setTimeout(() => console.log(2), 0);
console.log(3);
3. What is closure and its use and example.
4. What is the spread operator.
5. How can spread array and object.
6. Why we can use the spread operator.
7. What is authentication.
8. Which authentication is used to secure your APIs.
9. Why password is not added to the JWT token?
10. What are promises.
    1. If we want to call two APIs and send a response after completing both the APIs. How can we achieve it?
     2. If one of API call gets failed and we want to send both result to client then what method would be used?
11.  user collection:
[
  {name: "person a", skills: ['mysql', 'mongo', 'react'] },
  {name: "person b", skills: ['node', 'mongo', 'react'] },
...
]
1. Write a query to get all the user details with matching skills 'react' or 'mongo'
2. Write a query to get all the user details with matching skills 'react' and 'mongo'
1. Difference  between let, var, and const
2. Which promise method is used to execute all API calls parallel
3. What is the bind method and the difference between call and bind.
4. What will be the output of the following code and why?
function two() {
    console.log('myVar', myVar);
}
function one() {
    var myVar=2
    two()
}
var myVar=1
one()
5. What will be the output of the following code and why?
function printHello() {
    console.log('Hello')
}
printHello()
6. What will be the output of the following code and why?
printHello2()
var printHello2 = function() {
    console.log(' printHello2 Hello')
}
7. What is an event loop?
8. What will be the output of the following code and why?
console.log('Log first')
setTimeout(function(){console.log('Log second')},3000)
setTimeout(function(){console.log('Log third')},0)
console.log('Log fourth')
9. What is sharding in MongoDB?
10. Why MongoDB is better than SQL database?
11. What are the operators available in MongoDB?
12. What is unwind?
13. Find the second highest salary from the table
14. Find all the users having a role developer whose age is less than 27.
15.  What are authentication and authorization?
16.  Which authentication module is used in your project.
17.  Where you are storing the JWT token?
18. How do you manage expired JWT tokens?
19. After the token expires are you logging out the user from the app?
20. What is the other way to manage expired tokens so that users don't need to do logout and login again?
Last round of interview Asked about the following topics
Past projects
API standards
Security standards
Scaling Application
Managing multi-role functionality
Code review standards
*************************************************
what are the mongoose operators you have used
$skip
$size
2 what is closure?
3 how will you achieve api versioning?
4 functions used in unit testing
5 which Promise functions you have used like Promise.all()
6 advantages of nosql over sql
7 what is cluster in node js
[6:03 PM] output of following programs
for(var i=0;i<100;i++){
  setTimeout(()=>{console.log(i)},0)
}
let obj={foo:"bar"};
let obj1=obj;
obj1.foo=6;
console.log(obj1.foo)
console.log(obj.foo)
return toppers data from students table using mongoose query
js is synchronous or asynchronous ?
does javascript use oop?
[6:10 PM] what is $lookup in aggregation?
[6:14 PM] output for following prog
let number=0
console.log(number++)
console.log(++number)
console.log(number)
what is the difference between var and let?
what is the difference between arrow fun  and normal function?

const str=['Welcome', 'to', 'Programiz']
reverse every word and return array...
eg.   [ 'emocleW', 'ot', 'zimargorP' ]
4:11
without using inbuilt method
- Sort array by name
let arr = [
        {name:"sanket",value:"1"},
        {name:"aniket",value:"1"},
        {name:"yash",value:"1"},
    ]

- Find output bu using reduce method 
  let str = "i love india"
  OUTPUT => "ILI"
  
  Code 1:
const array=[1,2,3];
{
  1:1,
  2:4,
  3:9
}

Code 2: Using reduce

[4,5,6,7]

Code 3:

let c = { greeting: 'Hey!' };
let d;
d = c;
c.greeting = 'Hello';
console.log(d.greeting);

Code 4:

let c = 10;
let d;
d = c;
c= 11
console.log(d);

Code 5: 

var x = 21;
var girl = function () {
console.log(x);
var x = 20;
};
girl ();

Code 6:

function() {
console.log(1);
setTimeout(function(){console.log(2)}, 0);
setTimeout(function(){console.log(3)}, 1000);
console.log(4);
})();

Code 7:

var p = new Promise((resolve, reject) => {
        reject(Error('The Fails!'))
    })
    .catch(error => console.log(error))
    .then(error => console.log(error))
    var arr=[10,2,4,9,20,30];
 console.log(arr.sort((a,b)=>a-b)[0]);
