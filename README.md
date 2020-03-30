## Service : 
`ng generate service service_name` to generate the service name

So you always need to import the in the `app.module`
How you can do this ? 

1) When you check the `service-name.services.ts` file, you have got an constructer with the export class.
Just copy the same.

2) In app.module file add the providers name exactly what it is there in the Class name.

3) Import the service too, by using `import { ServiceNameService } from './service-name.service`