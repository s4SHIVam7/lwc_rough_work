# lwc_rough_work
some rough work


## Notes

## 1
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
  
## 2
Alert(not a toast) in lwc
- html
```
<template>
    <lightning-button onclick={handleAlertClick} label="Open Alert Modal">
    </lightning-button>
</template>
```

- js

```
import { LightningElement } from 'lwc';
import LightningAlert from 'lightning/alert';

export default class MyApp extends LightningElement {
    async handleAlertClick() {
        await LightningAlert.open({
            message: 'this is the alert message',
            theme: 'error', // a red theme intended for error states
            label: 'Error!', // this is the header text
        });
        //Alert has been closed
    }
}
```
- Screenshot
![image](https://github.com/s4SHIVam7/lwc_rough_work/assets/60181328/ac14ebd8-2c90-4364-a180-63ba782d70a9)

