#### Step 7 Change Component

With following example, we can see that a change in a file is detected immediately and the Appliction is changed accordingly:

`sed -r -i 's/Angular/World/g' src/app/app.component.ts`{{execute}}

![Hello World](https://oliverveits.files.wordpress.com/2017/06/2017-06-13-18_07_35-angular-quickstart.png)

In the Dashboard or the Browser, where you have opened the Client, 
"Hello Angular" is automatically exchanged by "Hello World". There is no need 
to reload the browser manually. You just need to wait for some seconds, 
depending on your Internet speed.

To toggle back and to 'Hello Anglar', you can issue the command 
`sed -r -i 's/World/Angular/g' src/app/app.component.ts`{{execute}}