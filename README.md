## Service : 
`ng generate service service_name` to generate the service name

So you always need to import the in the `app.module`
How you can do this ? 

1) When you check the `service-name.services.ts` file, you have got an constructer with the export class.
Just copy the same.

2) In app.module file add the providers name exactly what it is there in the Class name.

3) Import the service too, by using `import { ServiceNameService } from './service-name.service`


## Angular modules consist of a discrete set of attributes that you use to describe the module. These are listed here:

`declarations` - these are the list of components, directives, and pipes that are a part of the specific module you are creating. Everything in a declaration is visible to application using this module, without requiring any explicit exports.
`imports` - using import statements, you can make other modules visible within this module. Importing other modules is not an implicit export of those other modules, meaning simply, if another developer imports your module, they may not be able to see the modules you have imported.
`exports` - this is the list or any declarations that you want to be made available (visible) to other modules that may import this module.
`providers` - used to list providers for configuring the injector, when this module is imported by other modules.
entryComponents - constitutes a list of components about which ComponentFactory should be generated. Primarily used for dynamically loading components.

## Dependency Injection (DI) is a software design pattern that manages how components in a system obtain their dependencies. In Angular, Dependency Injection is responsible for:

1) Creating components
2) Maintaining a component's state
3) Providing components to other components, as required

## Note that we used the same name as when we generated the interface. You will note that the Angular generator automatically appends the type of object you are generating to the filename (e.g. service, component, module, etc.). This is useful as you can name related files similarly and keep those files in a single directory without worrying about naming conflicts.

## You can see that the Injectable decorator has been imported from @angular/core. This allows you to inject this service into other components. You can use this decorator on other types of classes, but it should always be included in a service.

## Now that we have our service ready to go, we can import the interface we made in the previous task. When we do this, we can give the Service the shape of the expected output of our API call, and every component that we subsequently inject our Service into will be provided with that information as well. This will especially come in handy later when we are building out the views for our application.

## Finally, to correctly identify the response with TypeScript, we need to annotate our method to include the proper types. In this case, our function is taking in a string and it's going to be returning a Promise with a return value that is a GitSearch - Promise<GitSearch>. We also need to mark that the response will have the shape of GitSearch by using the type assertion response as GitSearch.


## Components 
Angular follows the MVC architecture which stands for Model-View-Controller. The Model portion contains application data. The View is the user interface (UI) or the web page that a user interacts with. The Controller handles the interaction and communication between the View and the Model. In Angular, your component will interact with the view through an application programming interface (API). The APIs consist of properties and methods to act on those properties, or provide some functionality.

One of the most noteworthy and useful features of the Angular architecture is the usage of reusable components to display data. By using an Angular Component, you can couple data display logic, styles, and HTML into one container that's easily portable throughout your application.

An Angular component consists of a template, that is the view or “a” view layout for a portion of your web application. The template consists of HTML for the layout and is used to define the rendered content on the page.

The Angular code that you will add to this HTML is responsible for setting the bindings to data and the directives within the HTML that provides the dynamic aspects of an angular component.

Angular also makes use of a class file to contain code that supports the view in the template. Typically this class file will be created in TypeScript and will contain the properties and methods that will be used by your application.

You'll typically have a top-level component in your Angular application. In the tutorial labs, you will work on building a top-level component called git-search. The Angular CLI command is ng generate component which is followed by the component name you want to use such as ng generate component git-search.

This will result in a new folder structure being created in your Angular app's root folder. The folder structure will be /src/app/git-search in this instance. Within this folder, a number of files will be created:

a typescript file with the .ts extension to contain the logic for the component
a CSS file that is injected into the component for specifying styling using CSS for the component
an HTML file that will contain the view template
a Karma test file with the .spec.ts extension, in the event you want to implement Karma testing
When you open the .ts file, you will find these common aspects as a part of the component:

import { Component } from @angular/core

Import statements are used to access functionality in other code such as libraries and other classes. This line is responsible for importing the Component Object from the @angular/core library. This is one of the main libraries used in Angular.

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
  title: string = 'Page Title';
}) 
This is segment where you define your component. The @ is a TypeScript symbol that helps us describe an Angular directive. In this case, @Component is a directive that tells Angular we wish to create a new component.

@Component is also known as a decorator. A decorate in Angular is prefixed with an @ symbol and is considered a mechanism to add metadata to a class, to the members of a class, or to method arguments of a class. You place the decorator before your class name, ie before the export statement. Angular has several built-in decorators and you will get a change to use some of them in this course.

Within the @Component body, we see a selector, templateUrl, and styleUrl entries with some values assigned. Let's cover each of these so you understand their purpose.

selector - this specifies the name of an HTML tag that will contain this component when the application is running. In the HTML, you will find <app-root></app-root> tags for this component
templateUrl - using this option allows you to specify a template that will contain the HTML for this component. You could also opt to use the template: option and specify “inline” HTML right in the body of the component.
styleUrls - this links to an external CSS style sheet that will be applied to the component's HTML rendering
There are other options available for the component and you can browse the Angular documentation for additional options and instructions on using them.

Everything found within the @Component section is considered to be metadata and template information for this component. Obviously the template information consists of the HTML elements that may be found within the component. In this instance, we are using a URL to define the template rather than placing the HTML inline in the component.

Next we set up an export statement like this:

export class AppComponent implements OnInit

The export keyword is what allows your component to be available to be imported into other files in the project. THe class keyword identifies this as a class file so if you are familiar with object-oriented programming, then you will understand that class is a keyword used to identify a file that contains the “blueprint” information for a reusable component.

The AppComponent identifier is the class name. It will be the name you use within an import statement in other areas of your application and offers a clear identifer for this class.

The last keyword, implements, will not always be present on all components. In this case, it indicates that our AppComponent class will also implement functionality that is specified in another component or interface, known as OnInit. We won't teach interfaces here but again, it is an object-oriented programming concept that is used to specify behavior of a class file based on behaviors defined in another file.

Also, this is where we define any variables or functions that the component will consist of. We can see an example here:

constructor (private GitSearchService : GitSearchService) {
    
  }
  ngOnInit() {
    this.GitSearchService.gitSearch('angular').then( (response) => {
      alert("Total Libraries Found:" + response.total_count);
    }, (error) => {
      alert("Error: " + error.statusText)
    })
  }
  title = 'GitHub Browser';`

Here we setup a constructor for our class, implement the ngOnInit() method, and set a title for the component.


Binding is the term used to describe how the data for our application is “connected” to the user interface. If we step back and review the MVC architecture again, we noted that the Model was defined as the data, the View as the UI, and the Controller as the application logic but also as the communicator between the data and the UI.

So, binding is responsible for the communication between our data and our UI. Our data can reside in a back-end database running on a server or it could be as simple as a flat file, such as a JSON file, that contains the data we want to use in our application.

Binding allows us to pass the data into the UI through the use of properties, in the class that defines our Model, and the use of directives, which make use of a concept known as interpolation. Interpolation is the mechanism used to represent a placeholder, in your template, for the data that will be displayed.

So, in summary, binding is the mechanism used to tie the data to the UI for display.

## Pipes 
A pipe allows you to use data, as an input to the pipe, and transform it to a more desirable output. As we think about our Angular applications, perhaps the most common reason for creating the application is to access and display data in our web applications. However, the data may be somewhat cryptic or not necessarily “user friendly” as in a data format.

Often times a date may come to in the form:

Sat Jun 20 2017 04:00:00 GMT -0800 (Pacific Standard Time)
While it is readable to a certain degree, not every user cares about the time, or the offset. Perhaps you want to display this in a different format that expands the month rather than using an abbreviation, or perhaps, you want to switch the day and month around to support a different locale. Pipes help you accomplish this.

Angular actually has a collection if built-in pipes for common tasks such as DatePipe, UpperCasePipe, LowerCasePipe, and CurrencyPipe. You can find out more about these in the API documentation for Angular. You will make use of the DatePipe and UpperCasePipe in the tutorial labs for this module.

As mentioned in Introducing Pipes, pipes are a concept in Angular that takes data and applies a transformation to it before sending it to the template to be rendered. This can be particularly useful for formatting purposes where consistent data transformations need to be applied to your data.

If you are familiar with command-line or shell environments in operating systems, you may also be familiar with the pipe symbol |. In the command-line environments, this pipe symbol is used to send the output from one command to another command. Likewise, in Angular, we are going to use the pipe symbol to transform the data in our template, by passing it through a pipe to a transformation.

In this code sample, taken from the labs, we will demonstrate applying the built-in date pipe to an Angular binding. The way we accomplish this is to add the pipe or | character after the Angular binding, followed by the built-in pipe command. The command we use here is date:'fullDate' to indicate a format of full date. See the code sample below:

<div *ngIf="searchResults; else elseBlock">
  ... 
      <p class="description"> {{result.description}}</p> 
      <p> Created On: {{result.created_at | date:'fullDate'}} </p>
    </li>
  </ul>
</div>
<ng-template #elseBlock>Loading...</ng-template>



## Introducing Directives

Angular directives are responsible for providing functionality in an Angular application and help transform the Document Object Model (DOM).

When you implement directives in your Angular application, you will use one of two types, structural directives or attribute directives.

Structural directives are what you use to modify the layout of the page by manipulating the DOM. An attribute directive will merely alter the behavior or appearance of an existing DOM element.


As we noted in the introduction to directives topic, structural directives manipulate the HTML layout through the DOM. The manipulation comes in the form of either adding, removing, or changing an element. You know you are using a structural directive if the name is preceded by an asterisk such as *ngIf.

The *ngIf directive is a built-in directive that comes “out-of-the=box” with Angular. So what do we use it for?

Well, the keyword “if” that is contained in the directive should give you some idea. This directive will evaluate a boolean expression and based on the result, it either shows or hides an HTML element, as in the following example.

Angular also has some built-in attribute directives that you can use, if you prefer to not create custom attribute directives. Perhaps one of the most commonly used is the ngClass attribute directive.

The ngClass directive is designed to allow you to dynamically apply CSS to an element. The directive uses an expression to evaluate the CSS to apply. An example will illustrate this better.

