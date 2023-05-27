## Overall Panel 

query to get success build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'SUCCESS' OR "build_result" = 'CompletedSuccess' ) AND $timeFilter 
```
query to get failed build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'FAILURE' OR "build_result" = 'CompletedError' ) AND $timeFilter 
```
query to get aborted build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'ABORTED' OR "build_result" = 'Aborted' ) AND $timeFilter 
```
query to get unstable build count 
```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND ("build_result" = 'UNSTABLE' OR "build_result" = 'Unstable' ) AND $timeFilter 
```

## Number of pipelines ran 

```
select count(DISTINCT project_name) FROM jenkins_data WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND $timeFilter 
```

## Total number of builds 

```
SELECT count(build_number) FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND $timeFilter 
```

## Avg Build time 

```
select build_time/1000 FROM jenkins_data WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND $timeFilter 
```

## Latest Build Status 

```
SELECT build_result FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND $timeFilter  ORDER BY time DESC LIMIT 1
```

## build details 
```
SELECT "build_exec_time","project_path","build_number","build_causer","build_time","build_result" FROM "jenkins_data" WHERE ("project_name" =~ /^(?i)$job$/ AND "project_path" =~ /.*(?i)$folder.*$/) AND $timeFilter 
```
