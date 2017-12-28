# helm-chart-tests-demo
Small demo helm chart with tests that validate the kubernetes yaml files that generated by the templates. 
The tests are written using [kubetest](https://github.com/garethr/kubetest), powerfull tool that let you easily write tests for those files.

## Running the tests
### Setting up
* Install [helm](https://github.com/kubernetes/helm/blob/master/docs/install.md)
* Install [helm-template](https://github.com/technosophos/helm-template)
* Install [kubetest](https://github.com/garethr/kubetest)

### Running
* `cd demo`
* Generate the files using `helm template . -f tests/values.yaml > template.yaml`
* Run the tests using `kubetest template.yaml --verbose`. 

## How does it works?
* the `demo/tests/values.yaml` file define various values for your template. 
`helm template` use this file to generate kuberenetes yaml. 
You can set here all the various configurations of your templates, and even have multiple values files for different tests.
* The tests, located at `demo/tests/tests.sky` running the validation on the configuration files.
Take a look at the test, it is pretty simple - testing the the `nameOverride` from the `values.yaml` actually used. Feel free to modify the tests and watch it broken.

## What missing?
* Docker file - with all the dependencies, to make it easier to run the tests
* Add CI to the demo, make it easier to understand how to run the tests
