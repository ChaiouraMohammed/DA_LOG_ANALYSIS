# DA_LOG_ANALYSIS
Server log analysis project using Python to explore web traffic, performance metrics, and security patterns through data preprocessing, visualization, and exploratory data analysis.

## Focus point
In this project, i tried to focus specifically on detecting suspecious activities in a log file of a website that is already in production.
The analysis includes exploring IP addresses, HTTP requests and HTTP status code in order to identify unusual activities and abnormal user behavior.
## Columns 
```python
Index(['timestamp', 'server_id', 'method', 'path', 'status_code',
       'response_time_ms', 'bytes_sent', 'user_agent', 'ip_address',
       'referrer'],
      dtype='object')
```
