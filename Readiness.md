The [[POD Status]] can be [[POD Status#Ready]] but still not accessible, because Kubernetes assumes, that as soon as a container is created, the POD is ready to serve user traffic, even though the service (application) which is been acceesed is not warmed up. 

To solve this mismatch of application status and contianer status, we can use the `readinessProbe` attribute in the POD definition file.