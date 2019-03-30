# Edits

The option to only to do a 'shallow' download has been added to the download function. Just set 'isShallow' to True, and it will only download the next level of data. After that, you can construct the next level of keys, rinse, and repeat.

![fireData](http://frapbot.kohze.com/fireData/topImage6.jpg)

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/Kohze/fireData/master/LICENSE.txt)
[![Build Status](https://travis-ci.org/Kohze/fireData.svg?branch=master)](https://travis-ci.org/Kohze/fireData)
[![codecov](https://codecov.io/gh/Kohze/fireData/branch/master/graph/badge.svg)](https://codecov.io/gh/Kohze/fireData)


**Project Title:** FireData: Connecting R to Google Firebase

---

FireData integrates R Datascience with the abilities and possibilities of the Google Firebase Framework.

Firebase makes it possible to exchange in real-time information in the Cloud and thereby opening the R language to IoT hardware/data processing. Other than that it is also immensely useful for shiny application to integrate Social Authentications and persistent data & uploads.

This package was created within the framework of Google Summer of Code 2017 and 2018.

![fireData](http://frapbot.kohze.com/fireData/setup2.jpg)

**Database Setup:**
- visit https://firebase.google.com/
- login and enter the "console"
- add new project
- find the API keys at the "overview" page clicking on add firebase to web-app
- certain functions requires OAuth 2.0 access which needed client_id and client_secret, these can be found from the [google developer console](https://console.developers.google.com/apis/credentials)

**R Package Setup:**

```
if (!require("devtools")) install.packages("devtools")
devtools::install_github("Kohze/fireData")

library(fireData)
```

![examples](http://frapbot.kohze.com/fireData/examples2.jpg)

**Authentification**

- using anonymous login

```r
token <- anonymous_login(project_api = "AIzaSyAjZLO9-CRV3gObpwdFz-k8AiTOxHSBmdc")

token$idToken
```

**General Functions:**

- uploading a data.frame:

```upload(x = mtcars, projectURL = "https://firedata-b0e54.firebaseio.com/",  directory = "main")```

- patching a data.frame:

```patch(x = mtcars, projectURL = "https://firedata-b0e54.firebaseio.com/",  directory = "main/-KxwWNTVdplXFRZwGMkH")```

- putting a data.frame:

```put(x = mtcars, projectURL = "https://firedata-b0e54.firebaseio.com/",  directory = "main/-KxwWNTVdplXFRZwGMkH")```

- download a data.frame:

```download(projectURL = "https://firedata-b0e54.firebaseio.com/", fileName = "main/-KxwWNTVdplXFRZwGMkH")```

- register a new user

```createUser(projectAPI = "AIzaSyAjZLO9-CRV3gObpwdFz-k8AiTOxHSBmdc", email = "your@email.com", password = "12341234" )```

- create token for authenticated requests (can be used for the token argument of upload/download)

```auth(projectAPI = "AIzaSyAjZLO9-CRV3gObpwdFz-k8AiTOxHSBmdc", email = "robin@kohze.com", password = "12341234")```

- reset user password

```resetPassword(projectAPI = "AIzaSyAjZLO9-CRV3gObpwdFz-k8AiTOxHSBmdc", email = "useYourOwn@email.com")```

- backup the database and save as .json

```dataBackup(projectURL = "https://firedata-efa5a.firebaseio.com", secretKey = "2bYA6k72wKna90MqPGa6yuMG7jAysoDJZwJqYXsm", "test.json")```





![fireData](http://frapbot.kohze.com/fireData/related2.jpg)

fireData is already integrated into a several projects.

- SpatialMaps: A spatial proteomics platform that utilizes firebase as cross platform database.

- Cryptotrade-hq bot: A simple data collector (with shiny) that uses firebase for secure storage of API keys.


![fireData](http://frapbot.kohze.com/fireData/development2.jpg)

We are currently planning to add the new Cloud Firebase database and enhance the integration into R web applications.

---

**Aknowledgements:**

I hereby want to thank my GSOC mentors L. Pedraza, S. Schmidt for their project support and especially L. Gatto for his insights and experience to make this package a reality.
