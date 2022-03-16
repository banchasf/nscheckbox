# Android app crashes when @nstudio/nativescript-checkbox is imported in the app NgModule
The following steps are to reproduce the issue:
1. Create a simple nativescript mobile app from the template

   ``` ns create nsmscheckbox --template @nativescript/template-master-detail-ng ```

2. Add the plugin @nativescript/template-master-detail-ng to the project
   
    ``` ns plugin add @nstudio/nativescript-checkbox ```
3. Import the @nstudio/nativescript-checkbox to app NgModule as the code below:

    ``` 
        import { TNSCheckBoxModule } from '@nstudio/nativescript-checkbox/angular';
        @NgModule({
             bootstrap: [AppComponent],
             imports: [NativeScriptModule, AppRoutingModule,TNSCheckBoxModule],
    ```
4. Run the command as a sample below to verify the build in Android emulator
    ```
     ns run android --release --key-store-path ~/Documents/abc.jks --key-store-password "123" --key-store-alias ksa --key-store-alias-password "ksap" --env.uglify --env.environment=beta --env.aot

   ```
   After the splash screen is displayed, the app will be crashed. However, it is working fine when it is run with the command
   
   ``` ns debug android```