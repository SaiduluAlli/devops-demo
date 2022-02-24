#This is the installation file for drupal deployment and service using helm3 charts.
#1. Install Postgres database first
#2. Build and install drupal 
    #a. helm create drupal
    #b. Fix deployment.yaml and service.yaml into templates/
    #c. Create variables in values.yaml and update Chart.yaml (description)
    #d. Add pv.yaml into templates/
    #e. Add pvc.yaml into templates/
    #e. helm template ./drupal (see how the deployment in yaml looks like and fix any errors)
    #e. helm lint ./drupal (check schema of redis app)
    #f. Fix any errors and run helm lint ./drupal again until errors are clear
    #g. cd to ../drupal
    #h. helm install my-drupal-release ./drupal (to install redis deployment/service/volume)
    #i. helm list -a (list out your helm installations)
    #j. kubectl get all (see deployment, service, pod and volume - see my-drupal-release)
    #k. helm uninstall my-drupal-release ./drupal (to uninstall redis deployment/service/volume)
    #l. helm delete <my-drupal-release> (This will delete the installation of redis from the helm list command)

    #m. kubectl get all (Check to make sure services are running like below:) 
    #n. service/my-drupal-release          NodePort    10.109.86.51     <none>        80:30884/TCP     11m
    #o. deployment.apps/my-drupal-release             1/1     1            1           11m
    #p. pod/my-drupal-release-75f88f84c8-clzzt             1/1     Running   0               11m

#3. Configure drupal to communicate with postgres database.
    a. Go to site-> http://localhost:30080 (notice drupal installation come up)
    b. Choose Postgres install, db_name: dropal_production, user_name: drupal, db_password: drupal
    c. Click on Advanced tab->  host: postgresql (get it from containers->name: postgresql in postgres.yaml file)
    d. Proceed to install site
        A. site name: infinitedrupal, 
        B. site email: wnader@infinite.com 
        C. username: drupaladmin (maintenance acct name), password: drupaladmin (not this: drupal1234!@#), 
        D. confirm password: drupaladmin, default country: USA, default timezone: New York, 
        E. check for updates: [yes], receive email notifications: [yes]

    e. You should now be redirected to: http://127.0.0.1:30080/ (Welcome to infinitedrupal website)
    f. Click on various tabs to check content: 
        A. Content, Structure, Appearance, Extend, Configuration, People, Reports, Help
    g. Check code into repository

#4. Test the application 
    a. Go to: http://localhost:30080
