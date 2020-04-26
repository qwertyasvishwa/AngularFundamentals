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

