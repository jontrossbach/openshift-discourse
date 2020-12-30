# openshift-discourse
This is an automated deployment of discourse for OpenShift

Not working yet but when it does work it should launch by doing:

`oc new-app -f openshift/discourse.yml -e MAIL_FROM=<handle>@redhat.com`
