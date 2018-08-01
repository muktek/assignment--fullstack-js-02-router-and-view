# Full Stack JS Project
**`fullstack-js-02-server-router`**


## Context
You are going to build a full stack web application with node.js + React. In order to become familiar with how a node project works, you will be responsible for configuring the  initial major components of the project.  

- express server
- **application routes [this assignment]**
- views
- api layer
  - data access
  - data models (ORM)
  - RESTful routes

## The Assignment

For this assignment, we will focus on creating/configuring the **express router** and the router files to server simple html text and json data. See the 'Overview' section for explicit instructions of what to do and the 'Expected Results' of expected output/functionality.

### Deliverable

You will need to push your code to github on the `part-02-server-router` git branch for your `project--devjobs` repository

```
git add .
git commit -m '«your commit msg»'
git push origin --all
```

### Setup Instructions

In Terminal:

```sh
# (1) navigate to your project--devjobs directory
cd ~/Documents/muktek/assignments/project--devjobs

# (2) Commit your changes from the previous demo
git commit -m 'committing work from part-01'

# (3) Merge your changes from part-01 branch
git checkout master
git merge part-01-app-server

# (4) You will create the part-02-router branch for this feature
#      and complete your work there.      
git checkout -b part-02-server-router

```

### Overview

- Configure the express router to serve the following routes:
  ```
  /                  : '<h1>HOME page</h1>'
  /about             : '<h1>ABOUT Page</h1>'
  /api/jobs          : json - jobsData
  /api/companies     : json - companies

  * No Match *       : '<h1>404 - Page Not Found!</h1>'
  ```

- Serve the `<h1>404 - PAGE NOT FOUND</h1>` text when there is no match

### Requirements

- you must create a `routers/` directory in `src/`

- you must create 2 router files in the `routers/` directory:
  - `pageRouter.js`
  - `apiRouter.js`

- you must initialize the `express.Router()` in the 2 router files, and export the routers in `module.exports`
  - for `pageRouter.js`
    - `/` route should send the simple string `<h1>HOME page</h1>`
    - `/about` route should send the simple string `<h1>ABOUT page</h1>`
  - for `apiRouter.js`
    - `/api/jobs` route should send _`jobsData`_ as JSON (see 'Extra' section below)
    - `/api/companies` route should send _`companiesData`_ as JSON (see 'Extra' section below)

- the routes must be imported in `server.js` and passed correctly to `app.use(....)`

- In `server.js`, declare the default route behavior. You should have a default route-handler if a client requests a route.
  - The default route should respond with the simple string `<h1>404 - PAGE NOT FOUND</h1>`

- in `server.js`
  ```js
  // 1 - IMPORT THE ROUTES
  //     (note: you will need to write the actual path)
  var pageRouter = require('./path/to/pageRouter.js')
  var apiRouter = require('./path/to/apiRouter.js')

  // 2 - Apply the routes
  app.use('/', pageRouter);
  app.use('/api', pageRouter);


  // 3 - DEFAULT ROUTE
  app.use( /* write default route function*/ )
  ```


### Expected Results

1. When I go to `http://localhost:3000` in my browser, I should see text '_HOME page_' in an `h1` tag

2. When I go to `http://localhost:3000/about` in my browser, I should see text '_About page_' in an `h1` tag  

3. When I go to `http://localhost:3000/api/jobs`, I should see the following JSON in my browser:
  ```js
  [
    {
      "title": 'SQL Server Administrator - Postgres',
      "description": 'Bring to the table win-win survival strategies to ensure proactive domination. User generated "content" in real-time will have multiple touchpoints for offshoring.',
      "location": 'Guadalajara',
      "salary": 27000,
      "fullTime": true,
      "companyId": 1
    },
    {
      "title": 'UX Engineer',
      "description": 'Override the digital divide with additional clickthroughs from DevOps. Leverage agile frameworks to provide a robust synopsis for high level overviews.',
      "location": 'Monterrey',
      "salary": 35000,
      "fullTime": true,
      "companyId": 1
    }
    ...
  ]
  ```

4. When I go to `http://localhost:3000/api/companies`, I should see the following JSON in my browser:
  ```js
  [
    {
      "name": 'Company ABC',
      "description": 'Energistically network alternative technology deploying impactful partnerships.',
      "imageLink": 'http://www.tinygraphs.com/labs/isogrids/hexa16/nsuaio',
      "location": 'Guadalajara'
    },
    {
      "name": 'Lossless Enterprises',
      "description": 'Quickly strategizing team driven "outside the box" thinking.',
      "location": 'Ciudad de Mexico',
      "imageLink": 'http://www.tinygraphs.com/labs/isogrids/hexa16/8282',
    }
  ]
  ```

5. When I go to `http://localhost:3000/idontexist`, I should see the text '404 - Page Not found' in my browser.


### Extra

#### _`jobsData`_

```js
[
  {
    title: 'SQL Server Administrator - Postgres',
    description: 'Bring to the table win-win survival strategies to ensure proactive domination. User generated content in real-time will have multiple touchpoints for offshoring.',
    location: 'Guadalajara',
    salary: 27000,
    fullTime: true,
    companyId: 1
  },
  {
    title: 'UX Engineer',
    description: 'Override the digital divide with additional clickthroughs from DevOps. Leverage agile frameworks to provide a robust synopsis for high level overviews.',
    location: 'Monterrey',
    salary: 35000,
    fullTime: true,
    companyId: 1
  },
  {
    title: 'API Architect',
    description: 'Collaboratively administrate turnkey channels whereas virtual e-tailers. Objectively seize scalable metrics whereas proactive e-services.',
    location: 'Ciudad de Mexio',
    salary: 39000,
    fullTime: true,
    companyId: 2
  },
  {
    title: 'Mid-Level Front End Engineer',
    description: 'Interactively coordinate proactive e-commerce via process-centric "outside the box" thinking. Completely pursue scalable customer service through sustainable potentialities.',
    location: 'Ciudad de Mexico',
    salary: 21000,
    fullTime: false,
    companyId: 2
  }
]
```

#### _`companiesData`_
```js
[
  {
    name: 'Company ABC',
    description: 'Energistically network alternative technology deploying impactful partnerships.',
    imageLink: 'http://www.tinygraphs.com/labs/isogrids/hexa16/nsuaio',
    location: 'Guadalajara'
  },
  {
    name: 'Lossless Enterprises',
    description: 'Quickly strategizing team driven "outside the box" thinking.',
    location: 'Ciudad de Mexico',
    imageLink: 'http://www.tinygraphs.com/labs/isogrids/hexa16/8282',
  }
]
```
