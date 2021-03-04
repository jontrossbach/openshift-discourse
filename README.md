# openshift-discourse
This is an automated deploment of discourse for OpenShift

To get it working (with the optional email environment variable):

`oc process -f openshift/discourse.yml -p PROJECT_NAME=anchovy-discourse-project-6 -e MAIL_FROM=<you>@redhat.com | oc create -f -`

The postgresql extensions needed by discourse need to be done manually:

`oc get pods | grep postgresql-1-`

`oc rsh pod/<postgresql-1-######>`

`$ psql`
`S \c discourse`
`$ CREATE EXTENSION hstore;`
`$ CREATE EXTENSION pg_trgm;`
`$ \q`
`$ ctrl-D`


Currently one must manually kick off the build for the custom s2i Dockerfile which should allow the deployment of discourse to begin on its own in about 10 minutes. 

When the deployment completes:

`oc get routes`

Use the Host/Port name with http:// in front of it to create and environment variable in the discourse pod:

`oc get pods | grep discourse`

`oc rsh pod/<discourse-#-######>`

`$ DISCOURSE_SITE_URL=http://<Host/Port>`




