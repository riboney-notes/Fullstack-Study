# Misc stuff

- [youtube channel java college](https://www.youtube.com/channel/UCt-Wvc_ojTzGLpjhruIXYSw/playlists)
- [java packager exe](https://adam-carroll.medium.com/java-packager-with-jdk11-31b3d620f4a8)
- [enterprise messaging](https://www.oreilly.com/library/view/enterprise-integration-patterns/0321200683/)
- [java concurrency](https://jcip.net/contents.html)
- [java roadmap](https://github.com/fChristenson/java-roadmap)
- [java logger](https://www.marcobehler.com/guides/java-logging)
- [string concat performance](https://redfin.engineering/java-string-concatenation-which-way-is-best-8f590a7d22a8)
- [fluent vs builder](http://www.javabyexamples.com/builder-vs-fluent-interface/)

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
