####Forked from 
https://github.com/stakater/dockerfile-logrotate/


###Kubernetes manifest files froked from https://github.com/stakater-charts



###usage 

Please change the log location from configMap.yaml  and schedule time from daemonset 
`          - name: CRON_SCHEDULE
            value: "0 5 * * *"`


kubectl appply -f configMap.yaml 
kubectl appply -f daemonset.yaml 

it will create a namespace `kube-logrotate` and install the daemonset for all nodes include master nodes. 

Please check the log

`
kubectl exec -it -n kube-logrotate logrotate-xyz bash 

tail -f /var/log/crontab 
`

 



