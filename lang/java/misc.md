# Misc stuff

- [youtube channel java college](https://www.youtube.com/channel/UCt-Wvc_ojTzGLpjhruIXYSw/playlists)
- [java packager exe](https://adam-carroll.medium.com/java-packager-with-jdk11-31b3d620f4a8)
- [enterprise messaging](https://www.oreilly.com/library/view/enterprise-integration-patterns/0321200683/)
- [java concurrency](https://jcip.net/contents.html)
- [java roadmap](https://github.com/fChristenson/java-roadmap)
- [java logger](https://www.marcobehler.com/guides/java-logging)
- [string concat performance](https://redfin.engineering/java-string-concatenation-which-way-is-best-8f590a7d22a8)
- [fluent vs builder](http://www.javabyexamples.com/builder-vs-fluent-interface/)
- [bit flags in java](https://www.experts-exchange.com/articles/1842/Binary-Bit-Flags-Tutorial-and-Usage-Tips.html)
- [bitflags and enumsets](https://eddmann.com/posts/using-bit-flags-and-enumsets-in-java/)
- [big 0 performance](https://stackoverflow.com/questions/2307283/what-does-olog-n-mean-exactly/2307314#2307314)
- [clean code & validation](https://ducmanhphan.github.io/2019-12-22-Clean-code-with-validate-input/#validating-method-input)
- [callback ex](https://medium.com/@pra4mesh/callback-function-in-java-20fa48b27797)
- [reactive programming](https://springframework.guru/reactive-streams-in-java/)
- [jpms naming](https://blog.joda.org/2017/04/java-se-9-jpms-module-naming.html)
- [jpms commaind line](https://nipafx.dev/five-command-line-options-hack-java-module-system/)
- [functional programming](https://medium.com/swlh/a-new-java-functional-style-f522dad40d32)
- [java pass by value](https://www.javadude.com/articles/passbyvalue.htm)
- [java DI](https://www.baeldung.com/java-ee-cdi#overview)
- [getresourceasstream is null](https://stackoverflow.com/questions/49702287/getresourceasstream-returning-null-in-java-10)
- [getresources as stream](https://stackoverflow.com/questions/47613602/java-9-0-classloadergetresourceasstream-nullpointerexception)
- [classloader](https://stackoverflow.com/questions/61316839/getclassloader-getresourceasstream-not-work-in-modular-java-project-openjdk)
- [IoC and DI pattern](https://martinfowler.com/articles/injection.html)
- [java junit with system](https://stefanbirkner.github.io/system-rules/)
- [tdd](http://agiledata.org/essays/tdd.html)
- 
```java
// This code snippet goes through all the field members of an object
private class ValidateCharacterSet {
        private void validate() throws Exception {
            List<String> errorList = new ArrayList<>();
            Class characterSet = CharacterSet.this.getClass();
            Field[] fields = characterSet.getDeclaredFields();

            // Log all fields
            for (Field f : fields) {
                errorLogBlankField(f, errorList);
            }

            if(!errorList.isEmpty()){
                logErrorMessages(errorList);
            }
        }

        private void logErrorMessages (List<String> errorList) throws Exception{
            Exception ex = new Exception();
            for(String error: errorList){
                ex.addSuppressed(new Exception(error));
            }
            throw ex;
        }

        private void errorLogBlankField(Field field, List<String> errorList) throws IllegalAccessException {
            if (field.getType().getSimpleName().equalsIgnoreCase("string") && ((String) field.get(CharacterSet.this)).isBlank()) {
                errorList.add(field.getName() + " is blank");
            }
            if (field.getType().toString().equalsIgnoreCase("int") && ((Integer) field.get(CharacterSet.this) == 0)) {
                errorList.add(field.getName() + " is 0");
            }
        }

// Same as above, except it uses switch statements and does not log error (returns boolean instead)

	 public boolean areFieldsNull() throws IllegalAccessException {
        Class guitar = Guitar.this.getClass();
        Field[] fields = guitar.getDeclaredFields();
        for(Field f: fields){
            if(isFieldNull(f)){
                return true;
            }
        }
        return false;
    }

    private boolean isFieldNull(Field field) throws IllegalAccessException {
        String type = field.getType().getSimpleName().toLowerCase();
        switch(type){
            case "string":{
                String value = (String) field.get(Guitar.this);
                return value.isBlank() || value.equals(null);
            }
            case "int":{
                int value = (Integer) field.get(Guitar.this);
                return value == 0;
            }
            default:{
                System.out.println("Method could not test for field type! Add the type to the switch statement!");
                return false;
            }
        }
    }

```

Iterator
```java
// Using Iterator
	 public Guitar getGuitar(String serialNumber){
        for(Iterator<Guitar> i = this.guitars.iterator(); i.hasNext();){
            Guitar guitar = i.next();
            if(serialNumber.equals(guitar.getSerialNumber())){
                return guitar;
            }
        }
        return null;
    }
```

using optional
```java
				// Create Config object; only meant for main method
        public static Config instance(String fileName){
            Optional<Config> config = Optional.empty();

            try{
                config = Optional.of(new Config(fileName));
            } catch (Exception e){
                System.out.println(e.getMessage());
            }

            return config.orElseThrow();
        }
```

behavior parameterization
```java
//    public static boolean messageIsValid(CommandEvent event, Predicate<Message> predicate){
//        return predicate.test(event.getMessage());
//    }
```
