# lwc_rough_work
some rough work


## Notes

Child to Parent Communication

1. **Create Child Component**:
   - helloWorld.html:
     ```
     <template> Hello, {firstName}! </template>
     ```
   - helloWorld.js:
     ```
     import { LightningElement } from "lwc";

     export default class HelloWorld extends LightningElement {
       @firstName = "Shivam";
     }
     ```

3. **Create Parrent Component**:
   - app.html
   - To view your component, add it to the app.html file.
     ```
      <template>
      	<div class="app slds-p-around_x-large">
      		<div class="slds-p-top_large">
      			<c-hello-world class="slds-text-heading_medium"></c-hello-world>
      		</div>
      		<h1 class="slds-text-heading_large" style="color:Tomato">{title}</h1>
           </div>
      </template>
     ```
     - ```<c-hello-world> </c-hello-world>``` is nothing but including child component in parrent component.

4. **ScreenShot**:
   - ![image](https://github.com/s4SHIVam7/lwc_rough_work/assets/60181328/c1d9a08c-3cc6-40df-9384-9f65c0305684)


