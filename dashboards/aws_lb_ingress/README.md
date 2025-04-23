# Application Load Balancer Ingress 

View exported Cloudwatch metrics for the AWS Load Balancer controller, broken down by the cluster, namespace, and target group. Because the generated target group names from the AWS Load Balancer controller are determined by `targetgroup/k8s-{{namespace}}-{{service}}-{{hash}}` the namespace variable is derived from the available target groups.

The dashboard relies on metrics exported by [Prometheus Cloudwatch Exporter](https://github.com/prometheus/cloudwatch_exporter). 

The full list of required metrics scraped from Cloudwatch:
```yaml
metrics:
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: RequestCount
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: ActiveConnectionCount
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_ELB_4XX_Count
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_ELB_5XX_Count
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_Target_2XX_Count
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_Target_3XX_Count
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_Target_4XX_Count
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: HTTPCode_Target_5XX_Count
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: NewConnectionCount
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: ProcessedBytes
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: RejectedConnectionCount
    aws_dimensions: [LoadBalancer]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: RequestCountPerTarget
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: TargetResponseTime
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
    aws_extended_statistics: [p20.00, p50.00, p70.00, p90.00, p95.00, p99.00]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: UnHealthyHostCount
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum, Average]
  - aws_namespace: AWS/ApplicationELB
    aws_metric_name: TargetConnectionErrorCount
    aws_dimensions: [LoadBalancer, TargetGroup]
    aws_statistics: [Sum]
```