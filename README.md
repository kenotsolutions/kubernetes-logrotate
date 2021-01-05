After creating a new Kubernetes cluster, an important task to do is to implement log rotation. Otherwise, the disk space may run out and affect the health of the cluster. I encountered an issue related to log rotation. I used here stakater solutions but it did not work so I made some changes and tested.

Tolgay Gul


####Forked from 
https://github.com/stakater/dockerfile-logrotate/


###Kubernetes manifest files froked from https://github.com/stakater-charts



###usage 

Please change the log location from configMap.yaml  and schedule time from daemonset 
`          - name: CRON_SCHEDULE
            value: "0 5 * * *"`


Please read to understand the logrotate parameters 
https://medium.com/stakater/logrotate-manage-logs-easily-45d19be7fcfe


kubectl appply -f configMap.yaml 
kubectl appply -f daemonset.yaml 

it will create a namespace `kube-logrotate` and install the daemonset for all nodes include master nodes. 

Please check the log

`
kubectl exec -it -n kube-logrotate logrotate-xyz bash 

tail -f /var/log/crontab 
`

 



