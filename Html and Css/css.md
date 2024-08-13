Selectors in CSS:

1. class (.user-details)
2. id (#user-id)
3. element ( p )
4. attribute ( [src] {} )

```
    <img src="angular.png">

    [src="angular.png"] {
    width: 300px;
    height: 200px;
    border: 3px solid tomato;
    }
```


```
    <prathamesh savant>
      Lorem ipsum dolor sit amet consectetur, adipisicing elit. Aut, minima!
    </prathamesh>


// css
  
  [savant] {
    color: tomato;
  }

```

#### Specificity:

Specificity Hierarchy
Every CSS selector has its place in the specificity hierarchy.

There are four categories which define the specificity level of a selector:

1. Inline styles - Example: <h1 style="color: pink;">
2. IDs - Example: #navbar
3. Classes, pseudo-classes, attribute selectors - Example: .test, :hover, [href]
4. Elements and pseudo-elements - Example: h1, ::before

* How to Calculate Specificity?

Start at 0, add 100 for each ID value, add 10 for each class value (or pseudo-class or attribute selector), add 1 for each element selector or pseudo-element.

Note: Inline style gets a specificity value of 1000, and is always given the highest priority!

Note 2: There is one exception to this rule: if you use the !important rule, it will even override inline styles!


The universal selector (*) and inherited values have a specificity of 0 - The universal selector (*) and inherited values are ignored!


#### Inherit property

Below example first font-family will not apply on button font-family, because browser first apply body property then re-apply by-default
so for this use inherit property for over-ride by default. so it will take body font-family property.

```
  <body>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit facere
      similique maxime deleniti error accusantium quae rem velit aut quia, vitae
      corrupti est beatae temporibus enim at eaque cum rerum! Eum, eaque. Amet
      quis laboriosam, veniam quod nostrum cum accusamus dolorum tempora
      officiis odit aut. Voluptatum ullam dolore, ipsum, quia possimus deserunt
    </p>

    <button>Click me</button>
  </body>

// css

body{
    color:tomato;
    font-family: emoji;
   
}


button{
    font-family: inherit;
}

```


### Inline elements:

Width - when we apply width then it will take only content width extra width will not apply.

heigth - height not apply on content 

margin: left and right side margin apply but top and bottom not apply

padding: padding apply but if there is other elements whether it's block level or inline it will overlap on the other elements.

display:inline-block ==> using this we can apply height, width, margin to element and if we take new inline elements next to this element it will show, if there is space avaialable. 



* Replaced inline elements: img tag is repaced inline element because we can give height and width to it. They are external objects whose representation is independent of the CSS formatting model.

e.g img , INPUT, TEXTAREA, SELECT, and OBJECT, video , iframe , embed , fencedframe

* Non-Replaced inline elements : a, b, span, strong these kind of inline elements are non-replaced elements. we cannot apply height and width to these elements. 



#### Percentage (%) :

while using % for 
width - it will take parent width percentage
padding - same like width (parent width)
margin -  same like width (parent width)


border - (invalid) will not work with %
height - will not work with %

and parent should be in px if not then it's parent
should be in px 


font-size related to parent font-size (px)
means it will relatively increase or 
decrease as per parent font-size while 
we are using %





