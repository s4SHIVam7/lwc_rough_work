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

  
   We can change name via attribute also, take a example
      ````
      <div class="slds-p-top_large">
			<c-hello-world first-name="Web" class="slds-text-heading_medium" ></c-hello-world>
		</div>
here, we changed name using first-name attribute .
![image](https://github.com/s4SHIVam7/lwc_rough_work/assets/60181328/b26b8253-971f-4590-9cdf-ed32100cb241)


  
## 2
Alert (not a toast) in lwc
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

## 3
Suppose we have too many lightning input/button and you want onchange Event Handler on each lightning/button, then you we don't need to write seperate Event Handler for each lightning input/button.
we can use only one Event Handler method in js for thta you need to use name attribute for lightning-input/button in html.

ex.

**Unenhanced code.**

html
```
<div class="slds-p-around_medium lgc-bg">
	<lightning-input
        	type="text"
        	label="Enter Name 1:"
        	value={First_Name}
        	onchange={handle_First_Name_Change}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
		type="text"
        	label="Enter Name 2:"
        	value={Second_Name}
        	onchange={handle_Second_Name_Change}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
        	type="text"
        	label="Enter Name 3:"
        	value={Third_Name}
        	onchange={handle_Third_Name_Change}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
        	type="text"
        	label="Enter Name 4:"
        	value={Forth_Name}
        	onchange={handle_Forth_Name_Change}
      ></lightning-input>
</div>
```

JS
```
handle_First_Name_Change(event) {
	this.insertFirstName = event.detail.value;
}
handle_Second_Name_Change(event) {
	this.insertSecondName = event.detail.value;
}
handle_Third_Name_Change(event) {
	this.insertThirdName = event.detail.value;
}
handle_Forth_Name_Change(event) {
	this.insertFourName = event.detail.value;
}

```

**Enhanced code.**

html
```
<div class="slds-p-around_medium lgc-bg">
	<lightning-input
		name="First_Name"
        	type="text"
        	label="Enter Name 1:"
        	value={First_Name}
        	onchange={nameHandler}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
		name="Second_Name"
		type="text"
        	label="Enter Name 2:"
        	value={Second_Name}
        	onchange={nameHandler}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
		name="Third_Name"
        	type="text"
        	label="Enter Name 3:"
        	value={Third_Name}
        	onchange={nameHandler}
      ></lightning-input>
</div>
<div class="slds-p-around_medium lgc-bg">
      <lightning-input
		name="Forth_Name"
        	type="text"
        	label="Enter Name 4:"
        	value={Forth_Name}
        	onchange={nameHandler}
      ></lightning-input>
</div>
```
JS
```
nameHandler(event) {

	let {name, value}=event.target;

	if(name === 'First_Name') {
            this.insertFirstName = event.detail.value;
        }
	else if(name === 'Second_Name) {
            this.insertSecondName = event.detail.value;
        }
	else if(name === 'Third_Name) {
            this.insertThirdName = event.detail.value;
        }
	else if(name === 'Forth_Name) {
            this.insertForthName = event.detail.value;
        }
}

```
