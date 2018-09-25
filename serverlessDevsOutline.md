Serverless for Devs w/ Vue + AWS + Micronaut

From a developers perspective
 - We don't like managing servers
 - We like easy, push button, done
 - Focus on code not infrastructure

The Project
 - Visualize my watering data compared to actual weather conditions
 - Rachio smart sprinkler
 - Google Spreadsheet to hold data
 - IFTTT.com (If This Then That)
 - DarkSky weather API - historical actuals

Static Site
 - Vue, React, Angular, Ember, etc
 - Webpack bundler
 - Deploy as just files

Deploy Static Site
 - AWS S3 bucket w/ Cloudfront CDN
 - Github pages
 - Netlify, Surge

S3 Deploy
 - CLI command-line
 - Example circle CI setup

Lambda
 - Functions as a service
 - Node, Go, Java/Groovy/Micronaut, C#
 - No worrying about app servers for functional services

Micronaut
 - Spring Boot but lite
 - Built for APIs and Serverless

Lambda Deploy
 - Complicated Manual process
 - Micronaut manual options
 - Gradle AWS plugin
 - Docker
 - Terraform

Lambda Sweet Spot
 - AWS services glue
 - Event processing
 - IoT backends

Lambda Struggles
 - Spin-up time from cold start
 - Sudden scaling
 - Code Management Maturity
 - Use ECS EC2 

The Details
 - API Gateway in front of Lambda
 - Cloudfront
 - Dark Sky API limit caching

Other Thoughts
 - Security - Auth0/Okta
 - Messaging/Streaming
 - Storage/databases
 - API Gateways



** Notes **
http://sdkman.io/
`sdk install micronaut`
https://docs.micronaut.io/latest/guide/index.html#groovyFunctions
`mn create-function grachio --lang groovy`
IntelliJ - Enable annotation processing
Gradle AWS Plugin is already setup for you
`brew install awscli`
AWS signup
- complete security tasks, MFA(2FA), non-root users
- cli setup https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html
- test create first lambda https://docs.aws.amazon.com/lambda/latest/dg/get-started-create-function.html
- create role `lambda_basic_execution`
Modify gradle script - `role/service-role/lambda_basic_execution`
`./gradlew deploy`
`./gradlew invoke`
Add API Gateway Trigger
Change role to add cloudwatch permissions
Lambda proxy response object format
 - https://aws.amazon.com/premiumsupport/knowledge-center/malformed-502-api-gateway/
 - https://medium.com/@lakshmanLD/lambda-proxy-vs-lambda-integration-in-aws-api-gateway-3a9397af0e6d

Vue
 - https://cli.vuejs.org/guide/deployment.html#general-guidelines
 - https://github.com/multiplegeorges/vue-cli-plugin-s3-deploy
 - create s3 bucket `aws s3 mb s3://grachio`
 - S3 bucket permissions public read https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteAccessPermissionsReqd.html
 - s3 bucket enable website hosting
 - IntelliJ Vue plugin
 - CORS https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-cors.html
   - CORS only allows wildcard or single domain

Git - create and save to github repos

Google Sheets API
 - Enable API
 - API Key setup https://developers.google.com/sheets/api/guides/authorizing
 - Public read w/ API Key
   - Could do Oauth2.0 but didn't want to mess with it

Increase Lambda memory to 512 for metaspace on API call

Env Variables for keys

** Improvements **
Rachio API push to Kinesis and store in AWS
Separate Lambda for Sheets & DarkSky
Call Weather API and store value each day after watering
Save backups of API calls, just in case network dies
Lambda API Key to limit usage
CircleCI Build/Deploy on git commitsRachio API push to Kinesis and store in AWS
Separate Lambda for Sheets & DarkSky
Call Weather API and store value each day after watering
Lambda API Key to limit usage
CircleCI Build/Deploy on git commits

TODO:
Save backups of API calls, just in case network dies
Figure out What to Demo
Make Diagram of how all the pieces fit together