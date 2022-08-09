# I18Demo

* app.component.html
```html
<section>
  <article>
    <h1 i18n>Under Construction!</h1>
    <p>This page is under construction.</p>
  </article>  
</section>
```

#### Step 1: Install Localize
```
ng add @angular/localize
```

#### Step 2: Extract 

```
ng extract-i18n
```
* Note: This will create a file messages.xlf

* messages.xlf
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2">
  <file source-language="en-US" datatype="plaintext" original="ng2.template">
    <body>
      <trans-unit id="7496367199789781856" datatype="html">
        <source>Under Construction!</source>
        <context-group purpose="location">
          <context context-type="sourcefile">src/app/app.component.html</context>
          <context context-type="linenumber">3</context>
        </context-group>
      </trans-unit>
    </body>
  </file>
</xliff>
```
* messages.fr.xlf ( create a new file for french - copy messages.xlf and translate the text to french)
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2">
  <file source-language="en-US" target-language="fr" datatype="plaintext" original="ng2.template">
    <body>
      <trans-unit id="7496367199789781856" datatype="html">
        <source>Under Construction!</source>
        <target>En construction !</target>
        <context-group purpose="location">
          <context context-type="sourcefile">src/app/app.component.html</context>
          <context context-type="linenumber">3</context>
        </context-group>
      </trans-unit>
    </body>
  </file>
</xliff>
```


#### Step 3: Add the Configurations for locale in angular.json

```
      "i18n": { 
        "sourceLocale": "en-US", 
        "locales": { 
          "fr": "messages.fr.xlf" 
        } 
      }, 
      "architect": {
      
      .... 
      }
```

* Inside architect, configurations
```
 "en-US": { 
              "localize": ["en-US"] 
            }, 
            "fr": { 
              "localize": ["fr"] 
            } 
```

* Inside serve tag, configurations
```
 "en-US": { 
              "browserTarget": "i18-demo:build:en-US" 
            }, 
            "fr": { 
              "browserTarget": "i18-demo:build:fr" 
            }
```

#### Step 4: Run the server with different locale

* English
```
ng serve --configuration=en-US
```
![image](https://user-images.githubusercontent.com/2763774/183627874-d3fadb54-1773-44dc-9ae9-72cd9a49e4dc.png)



* French
```
ng serve --configuration=fr
```

![image](https://user-images.githubusercontent.com/2763774/183627722-21998d6c-d23d-4fbf-aa07-9c8db9230224.png)



