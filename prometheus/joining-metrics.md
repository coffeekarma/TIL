# Joining Prometheus Metrics

PromQL, the querying language for Prometheus, can get complex. Especially when trying to join multiple metrics together. 
Here is an advanced example of joining two metrics on a lable.

---

### Problem

Metric 1: node_meta
```
# Example result: 

node_meta{instance="10.0.1.49:9000",job="nodeexporter",node_id="370lr30wz6hzgc6e770zijrhv",node_name="MyServerName"}  1 
```

Metric 2: sum(rate(container_last_seen[5m])) by (container_label_com_docker_swarm_node_id)
```
# Example result: 

{container_label_com_docker_swarm_node_id="370lr30wz6hzgc6e770zijrhv"}
```

The lable node_id (Metric 1) and container_label_com_docker_swarm_node_id (Metric 2) have the same value on which we want to join but different names.

### Solution
To join two metrics in PromQL we use the expression `metric1 * on (exampleLable) metric2`. The exampleLable has to be the same in both metrics for this to work. 
To archive this we use the PromQL function `lable_replace` on Metric 2: 
```
label_replace(sum(rate(container_last_seen[5m]))  by (container_label_com_docker_swarm_node_id), "node_id", "$1", "container_label_com_docker_swarm_node_id", "(.*)") 
```
This adds a new label "node_id" to Metric2 with the value of "container_label_com_docker_swarm_node_id". Now both metrics have the same lablename and we can join them: 
```
label_replace(sum(rate(container_last_seen[5m]))  by (container_label_com_docker_swarm_node_id), "node_id", "$1", "container_label_com_docker_swarm_node_id", "(.*)")  * on(node_id) group_left(node_name) node_meta            
```
