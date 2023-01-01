# Faircorp Frontend VueJS

[Deployed Frontend on EMSE Gitlab Pages](https://github.com/TareqChy1/Faircorp-VueJS)

- Author :[Tareq Md Rabiul Hossain CHY](https://www.linkedin.com/in/tareqmdrabiulhossainchy/), [Nushrat JAHAN](https://www.linkedin.com/in/nushrat-jahan-3275a9178/) and [Erfan ENFERAD](https://www.linkedin.com/in/erfan-enferad/)
- VueJS Frontend App of the 2022 Web Programing project for [MSc CPS2 Web programming course](https://ci.mines-stetienne.fr/cps2/syllabus/)
- Based on [Quentin Richaud's course](https://gitlab.com/emse1/cours_js_1)

## Context

The goal of the 2022 Web Programing project is to implement a fully functional Smart Building management system (especially building, rooms, windows and heaters controllers).\
The project is composed of a [Java SpringBoot Backend server]() and a [VueJS Frontend server](https://github.com/TareqChy1/Faircorp-VueJS) interacting together. 


## Project setup or access via the [Deployed GitHub Page](https://github.com/TareqChy1/Faircorp-VueJS)
Install all the dependencies

```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

We locally run our Faircorp_Backend project in [localhost:8080](http://localhost:8080) and Faircorp_Frontend project in [localhost:8081](http://localhost:8081) 

NB : The frontend is supposed to work with the Spring Backend deployed on Clever-Cloud. If not or if anyone want to run the backend locally, anyone can configure the API's hostname in [./src/config.js](./src/config.js)

### Compiles and minifies for production
```
npm run build
```

** NOTE: This group project is cloned due to complete task for course unit "Technological foundations of software development" **