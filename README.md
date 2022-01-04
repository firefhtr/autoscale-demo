# autoscale-demo
Quick demo for Horizontal Pod Autoscaling (HPA) with a php-apache workload

Included are the yaml files for starting the php-apache workload and the HPA settings.  The workload will deploy into the 'default' namespace.
Status will be checked every 15secs

Here are the commands to test with (after deploying yaml files):
  # Get HPA status: 
        kubectl get hpa
  
  # Apply test workload pressure: 
        kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
  # Watch the HPA scale:
        kubectl get hpa php-apache --watch
  # Get deployment status:
    kubectl get deployment php-apache

Good Luck!
