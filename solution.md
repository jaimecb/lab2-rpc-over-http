# How to solve this lab

After forking the repository, I created a new branch named work, with the following command. 
```
git checkout -b work
```
Next, I modified my *.github/workflows/ci.yml*    file in order to build my work branch. 
```
push:
    branches: [ main , work ]
  pull_request:
    branches: [ main , work ]
```
Then, I tried to deploy the server and the client. You should ensure to deploy the server before the client, because otherwise you will run into problems.
```
gradle :server:bootRun
```
```
gradle :client:bootRun
```
If nothing else has been modified, both of them will throw an error because the server's transalation() function needs to be completed.
```
fun translation(@RequestPayload request: TranslationRequest): TranslationResponse = 
        TranslationResponse().apply() {
            translation = "hola"
        }
```
To match the server translation with the client, I've also modified the client`s input in the file *Client.kt*.
```
val input = "hello"
```
Finally, I've deployed the server and the client as explained, and the output's been the expected.