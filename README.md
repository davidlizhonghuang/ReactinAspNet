<h2>React used in asp.net mvc </h2>

<h3>Introduction</h3>

React is big that can be used to develop web and antive applications for all mobile devices. React invents React JS .net for asp.net web applications so .net developer can embed react capabilities in the front end of asp.net mvc web application.
Real IT world now is API everywehre one. Front end developer uses API to connect front end to middle tier. middle tier eveloper uses API to connect to data access layer that is supported by entity framework to connect to database in backend.
After code first or db first database is created, entity framework is plugged in to create data access layer. asp.net web api or microservice is used to create middle tier, finally asp.net mvc front end is introduced to build rich client front end web application for businesses.

Now, front end developers turn their attentions to React JS framework. React JS framework can be plugged into asp.net mvc to assist asp.net mvc development. Besides Razor views, asp.net mvc has one more view option that is React JS enabled HTML 5 front end.
This article will demonstrate the example I developed for React js in asp.net MVC.

<h3>Development</h3>

I have had developed an enterpriise based asp.net MVC web application for business. What I do here is to create a new empty asp.net mvc projec and nuget necessary react js libs. React controller and index.cshtml view are created for react enabled front end development.
in index.cshtml we embed React js links as below

<pre>
< script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.2/react.js"></script>
< script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.3.2/react-dom.js"></script>
</pre>

we then add a new index.jsx file. Visual studio 2015 already supports React so it is easy for use to add a new jsx file to scripts folder and add this jsx file into index.cehtml as below

<pre>
@section Scripts{ 
< script src="@Url.Content("~/Scripts/React/index.jsx")"></script>
 }
 </pre>

This is it. Now there are no any html tags in index.cshtml. We need to use React to add necessary html element/selectors in. This is the beauty of react we use here. We embed html elements to javascript and render them in html 5 page.

<h3>React component</h3>

There basicly are three ways to create React components for render.

1, Class
2, Function
3, Compnent

For example, I want to develop an img element in html. The component can be devleoped a three ways as below

1, class

<pre>
var Img = React.createClass({
    render: function () {
        return (
            < div>
                < img src="../Content/Images/122614018565928783.jpg" className="img-responsive" />
            < /div>
            );
    }
});
</pre>

2, Function

<pre>
function Img() {  
    return (
     <div>
                < img src="../Content/Images/122614018565928783.jpg" className="img-responsive" />
            </div>
    );
    }
</pre>

3, Compnent

<pre>
class Img extends React.Component {
    render() {
        return  < img src="../Content/Images/122614018565928783.jpg" className="img-responsive" />;
    }
}
</pre>

Then we can simply render all three ccomponents in one div as below

<pre>
ReactDOM.render(
  < Img/>,
  document.getElementById('root')
);
</pre>

<h3>React props</h3>

React component can consume json data from const, dummy data, and Web APIs, etc. React recommends a parse server in cloud as a backend.

component attribute is used to accept data from outside of the component as one example below

<pre>

var Comment = React.createClass({
    render: function () {
        return (
        < div className="comment">
        < h2 className="commentAuthor">
            {this.props.author}
        < /h2>
            {this.props.children}  
        < /div>
    );
    }
});

var CommentList = React.createClass({
    render: function () {
        return(
            < div>
                < Comment author="Daniel Lo Nigro">Hello ReactJS.NET World!</Comment>
                < Comment author="Pete Hunt">This is one comment</Comment>
                < Comment author="Jordan Walke">This is *another* comment</Comment>
          < /div>
            );
    }
});

</pre>

Here Comment component has an attribute "author" that accepts values from another component called CommentList. Comment itself then assign those values to its own children.
Therfore, Commment displays as below

<pre>

< div>
< div class="comment"><h2 class="commentAuthor">Daniel Lo Nigro</h2><!-- react-text: 8 -->Hello ReactJS.NET World!<!-- /react-text --></div>
< div class="comment"><h2 class="commentAuthor">Pete Hunt</h2><!-- react-text: 11 -->This is one comment<!-- /react-text --></div>
< div class="comment"><h2 class="commentAuthor">Jordan Walke</h2><!-- react-text: 14 -->This is *another* comment<!-- /react-text --></div>
< /div>

</pre>

This is the entry of outside data gets into component.From ehre we can simply create ajax call in componentDidmount function to fetch data from backend.

<h3>Page with React</h3>

Now a html page can be built via React js file as example below

<pre>
var WholePage = React.createClass({    
    render: function() {
        return (
          < div>
              < header />
              < content />
              < footer />
          < /div>
      );
    }
});

ReactDOM.render( 
  <WholePage />,
  document.getElementById('root')
);
</pre>


<h3>Summary</h3>

As I know, I do not believe React is a difficult thing we need to learn. It is easy if we know javascript and node js. React can push html elements to a browser as a page via javascript. React component is an object that has its own property and events we can develop to interact this component with outside world.
React js is only the one of front end technologies we can quickly learn and use in business development as Angular js which now is embedded into typescript in .net. React has its own advantages in mobile native application development as jquery for desktop devleopment.









