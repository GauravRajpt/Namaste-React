# NAMASTE REACT DAY 1 & DAY 2

## Hello world in html
```

<body>
    <div>
        <h1>hello world</h1>
    </div>
</body>

```
## Hello world in javaScript

```
<body>
    <div id="root"> </div>
   <script>
    const heading= document.createElement('h1');
    heading.innerHTML="Hello world";
    const container= document.getElementById('root');
    container.appendChild(heading);
   </script>
</body>
```
## Hello World using React
To use React in our code ,first we need to inject React library in our code.<br>
 there are several ways to do it and the one of the ways is inject through <u>CDN Links</u>

 To do this we will copy CDN Links from react offical website , and we'll put these in our code , it comes inside script tag.
 <br>

 as we put these Script tags inside our html code , now we have access of React's supper powers(functions or method).

 actually there are two scrits tag, one is for react and other one is for ReactDOM.

 we put our actuall script tag after these CDN links, because order is very important (so don't put your script tag before CDN scripts tag, otherwise it will so you error <u>Uncaught ReferenceError: React is not defined</u> ). Now we can code inside our script tags.

 ```
 <body>
    <div id="root"></div>
   
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script> 

const heading= React.createElement('h1',{},"Hello world");
const root=ReactDOM.createRoot(document.getElementById('root'));
root.render(heading);
</script>
</body>
 ```
/**React is comming from our cdn links and inside React there is a funtion called creatElement , here which will create an h1 element . syntax of CreatElements--- React.createElement(html tag, props, ...children).** / 
<li>if we have multiple children then we will write them inside [ ]</li>
<li>inside props we can write anything using key : "value" pair eg. {id:"headng"}</li>


<b>ReactDOM have a funtion createRoot which is responsible for creating a root for react Components </b>

<b>root.render()  append child inside root element. </b>


<h2><b>Q. </b>Using React create a div element and inside it create h2 html element with some text inside both h2</h2>

```
<body>
    <div id="root"></div>
   
<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
<script> 
const heading= React.createElement('h2',{},"Hello world");
const heading2= React.createElement('h2',{},"Namaste React");
const container= React.createElement(
    'div',
    {id:"container"},
    [heading,heading2])
const root=ReactDOM.createRoot(document.getElementById('root'));
root.render(container);
</script>

```
we get this warning: Warning: Each child in a list should have a unique "key" prop.

<b>What is key in React?<br>
A “key” is a special string attribute you need to include when creating lists of elements in React. Keys are used in React to identify which items in the list are changed, updated, or deleted. In other words, we can say that keys are used to give an identity to the elements in the lists</b>

now we just need to give key in props to both of our heading element to remove this warning.
```
const heading= React.createElement('h2',{key:"heading"},"Hello world");
const heading2= React.createElement('h2',{key:"heading2"},"Namaste React");
```

now we created a app, with a div & inside it we had created 2 div tags,
but is it a production ready app?
<br>"No"!<br>
so what it needs to be a production ready app?
* we need to minify our files.
* we nedd Hot reloading
* we need to compress our app
* we need to bundel things<br>
and we need to do a lot more things...<br>
to do all this workwe need something named as '<u>Bundler.</u>'
here are some example of parcel- vite, webpack, parcel
<br>
in this app we will be using 'parcel'.<br>
'in orginal creat react app 'webpack' is the bundler by default.'

At the end of day parcel is a package, & how do we install package in our system?-
<br>
We have to use a package manager, we can use any package manager but in this app we are using <u>npm</u>.

to use npm in our code ,we need to write this command on terminal : npm init 
<br>
this will ask some  question and then create a <u>package.json</u> file in our app.
<h3 style="color:red">inside package.json there is some configurations that npm uses to install dependencies, run scripts, and identify the entry point to our package.</h3>

if you want to skip questions then you can do this : npm init -y

<b>Q. why do we use npm?

Because we need a lot of packages in our app, and just injecting react in our app can not do all the things alone, so npm manages all the packages and these packages are present using npm.
</b>

<i>Now lets ignite our app</i>, to do this wee need to install a <b>Bundler</b>(package).

Let's install 'parcel'-<br>
npm install -d parcel

here we used -d because we do not want it in production we need it in our devlopment machine.
we are installing it as a dev dependency.


after doing this, we get <b>node_modules</b> and <b>package-lock.json</b> files in our app and inside package.json now we have:

"dependencies": {
    "parcel": "^2.8.2"
  }

okay, here 2.8.2 is the version of parcel. but whatis '^' <br> this is known as caret ,we can also use ~(tilde). if we do not use this it means we don't want any type of update of thid package.

<b><h3>What is package-lock.json?</h3>
package-lock. json file is essentially used to lock dependencies to a specific version number. This file is automatically generated (or re-generated) when there is a change in either the node_modules tree or package. json file.</b>

<b><h3 style="color:red">what is node_module?</h3></b>
<b>A node_modules directory contains all the React dependencies packages: react , react-dom , and their transitive dependencies like webpack , babal , rxjs , ESLint , etc., to build and run a React project.</b>

<h3 style="border: 1px solid yellow">Never push node_module file on github</h3>
<b>Git and npm provides an easy way to avoid pushing bulky node_modules to a GitHub repository using the .gitignore file and npm install command. A package.json file is the source to regenerate node_modules, so this file is enough to set up a fresh copy of a Node project.</b>

package-lock-json maintain the version of each and everything in node_module.

# Namaste react Day 3

<strong>Now i am going to say you that script tag of cdn is not a good way to get react in our code.<br></strong>
why?<br>
Because currently we are using version 18 of react. if in future we want to change version of react we have to change link inside script tag manualy, and it is not the faster way.
CDN links are slow because, because it is comming form anonther server, instead we can Install <b>React & ReactDOM</b> in our system.

React & ReactDOM will come as package in our system so we have to intall them using npm

```
npm install react
npm install react-dom
```
now let's ignite our app, to do this we need to write this command in terminal

```
npx parcel index.html
```
here npx means exicute npm , index.html is entry point of our app

<h3 style="color: red">actually i got this error after doing this <b style="background: black"> specified module not found, code:'err DLOPEN FAILED'</b>,  for one day i didn't find any solution , after than one gentle man tell me to install this:
<span style="color: blue">https://aka.ms/vs/17/release/vc_redist.x64.exe</span> now that error is no more occure , that gentleman said it is happening becuase 'Some dll files are missing while installing the vs code' and this link install all the neccesary files.
</h3>
after doing this so many things happen, we got 2 folder in our system- <b>dist and .parcel-cache</b>. and our app is runing on a localhost serverr , now we don't have to deal with , ugly files url.

but, now we get an err: react is not defined .

so fix this we import react and react-dom .whichever js file we want to use them.

now react and react-dom are not comming form another server , they are inside our node modules, thats why it is fast.

but we still get the same error, because our browser doesn't know about import, we have tell it that , this is not a normal js file inside script tag.
so in our script tag, we have to give <b>type="module"</b>.(module can import and export)

now everything is fine , and our browser is refresing itself,

wow, we are igniting our app, we got superpowers, and one of them is auto refresing.

and who is responsible for this supperpower , yes! 'parcel ' is a Beast.

what other supper power it gives us?
<br>
* HMR- hot module replacement
* file wathcer algorithm- c++
* cleaning our code
* minify our files
* super fast build algorithm
* image optimization
* chaching while development
* compression of files
* compaitable with older versions of browser
* HTTPs on development machine(npm parcel index.html-https)
* manage port number
* consistent hashing
* Zero config

we also got dist and parcel files, 

What goes in a dist folder?
The /dist folder contains the minimized version of the source code. The code present in the /dist folder is actually the code which is used on production web applications. Along with the minified code, the /dist folder also comprises of all the compiled modules that may or may not be used with other systems.

now i am deleting dist folder and running a command , 
```
npm parcel build index.html
```
here, we used build bcoz we now want to run it on production server.

now dist folder come again , and indside it few files.

dist bunle all our code in few files , that all we need for production.

<b>we should not push parcel-cache in git</b>.
<b style="color:green">anything we can genrate on server will be put inside git ignor</b>

<h2>'we can say that REact is PM Narendra modi and Parcel in Amit shah'</h2>
React has dependency on parcel(bundler) and parcel has dependency on other packages, this is called <b>transitive dependency</b>.

<h1>Day 4: Laying the foundation</h1>
<b>what is browserlist?
<p style="color:green">Browserslist is a tool that allows specifying which browsers should be supported in your frontend app by specifying "queries" in a config file.</p></b>
inside package.json we write like this:

```
browserlist{
    "last 2 chrome version"
    };
```
it means our code will definitly work on last 2 browser of chrome.

eg- some browsers are still not supporting ES6 , so our code will automatically replace with the pollyfill.

<b>what is pollyfill?<br>
This is code written in javascript that is compatable with browser, and work same as our code.
</b>

And who wrties the code for us ?

it is <b>bable</b>.

<h3 style="border: 2px solid yellow">parcel does Tree shaking(removing unwanted code).</h3>
suppose we import some library from some sever and it comes with a lot of functions, and in our code we just need one funtion, so parcel will remove all the unwanted code from our code and only that is needed will remain there.

currently Everytime we run our code we write:
```
npx parcel index.html
```
I found it messy . because i have to write it every time i run the code , and the good thing is we can change it using scripts- in package.json
```
"scripts":{
    "start":"parcel index.html"
};
//now we just need to run npm run start or we can just write
npm start
```
parcel or babel , doesn't remove console.log automaticaly from our code(to read more about this you can google : babel-plugin-transformation-remove-console).
<hr>


<b>React.createElements </b> gives us object , this object converts in HTML and then change the dom.

React=> createElements=>object=>HTML(DOM)

if we want to write huge html with .creatElements, this is not good , it will give us a headache.

- so instead of this JSX, facebook developers wrote it bcoz they got headache with creatElements.

```
const heading=(
    <h1 id="heading" key="heading">
    Namaste React
    </h1>
);
//this is perfectly wriiten jsx , creating h1 element and stroing inside js variable.
```
jsx has jsut HTML like syntax, we can write it inside our javascript file, it give us <b>readablity</b> and less stress.

<B>how jsx code work?<br>
jsx uses babel behind the scene , thats came from parcel in our code

babe uses React.createElement to creat heading, and as we know then creatElement gives and object , it converts into Html them add to the dom</b>
jsx(use babel)=>react.creatElement=>object=HTML(DOM)

Everything in react is component 
- funtional component(new)
- class based component (old)

but in this course we'll use functional component.

functional component is a javaScript component that returns react or jsx
```
const HeaderComponent=()=>{
    return <h1>Namaste</h1>
};
```
for good practice we start component Name with capital letter.
whenever we render react element we write like this 
```
root.render(heading)

```
and whenever we render our functional component we write like this:
```
root.render(<HeaderComponent/>)

// or we can write it like function call
 root.render(HeaderComponent());
 ```
if you want to write js inside jsx , you can write inside {}

if you use a component inside component it is called as <span style="color:green">Component Composition</span>
```
const Title=()=>(
    <h1>Namaste</h1>
);
const Header=()=>{
    return(
        <Title/>
        <h2>React</h2>
    );
};


