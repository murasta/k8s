https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/

kubectl get events

https://github.com/ahmetb/kubectx


apiVersion: batch/v1
kind: CronJob
metadata:
  name: python-counter
  labels:
    projekt: python
spec:
  concurrencyPolicy: Forbid
  successfulJobsHistoryLimit: 1
  schedule: "* * * * *"
  jobTemplate:
    metadata:
      labels:
        projekt: python
    spec:
      template:
        metadata:
          labels:
            projekt: python
        spec:
          containers:
          - name: hello
            image: nginx
            args:
            - curl
            - -XPOST
            - python-service/api/v1/info
          restartPolicy: Never




kubectl delete all,pv,pvc --all 