# cicd_learn

A new Flutter project.


This is my first project in which i integrate the CI/CD pipeline using Github Action.
No doubt, I couldn't add more data but as of now its enough to build apk automatic when we push 
code. There are so many things to do. you must read the blogs to learn more.

A few resources to get you started if this is your first Flutter project:

name: First CiCD  ## We gives the name of the workflow

on: ## this is the event when work flow work
push: ## if you push the code then is run
branches:
- main  ## this the the branch where this work flow work


jobs:  ## this is job which contain all the work
build:
name: Build Apk
runs-on: ubuntu-latest  ## here we gives the machine where this code run we can also give window 
and mac os
steps:
- uses: actions/checkout@v3 ## this command read our projects directory
- uses: actions/setup-java@v3
with:
distribution: 'oracle'
java-version: '17'
- uses: subosito/flutter-action@v2  ## this is for flutter 
with:
flutter-version: '3.24.3'
channel: 'stable'


## run commnad run the command in machine
- name: Install Dependency
run: flutter pub get 

- name: Build APK
run: flutter build apk --release

- name: Build appBundle
run: flutter build appbundle


