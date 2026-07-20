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
## Visuals / analytics
<img width="580" height="455" alt="image" src="https://github.com/user-attachments/assets/5d7b6695-a049-47d0-9a58-f2fc94ee0247" />\
As shown in the graph , HTTP status code 200 is the dominant status code in the dataset, with more than 3,500 successful requests recorded. This indicates that the majority of client requests were processed successfully by the server.
\
\
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/8e9e345c-1f8b-43eb-94ce-cf40fa533f57" />
The graph shows that the About page is the most visited section of the website, with a total of 191 requests.
\
\
Using this code, I created a visualization to make it easier to identify the most frequent HTTP status code for each path.
```python
status_by_path = (data.groupby(["path", "status_code"]).size().unstack(fill_value=0))

status_by_path.plot(kind="barh",stacked=True,figsize=(12, 10))

plt.title("HTTP Status Codes per Path")
plt.xlabel("Number of Requests")
plt.ylabel("Path")
plt.legend(title="Status Code")

plt.tight_layout()
plt.show()
```
\
\
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/978c1cb8-92cb-41bc-a253-c6b7f6b4054d" />
\
\
While this table shows the exact number of requests made for each path and HTTP status code.
\
\
<img width="1165" height="870" alt="image" src="https://github.com/user-attachments/assets/cd7461e0-a408-45b2-8db8-553caf04d06c" />

### The error request distribution 
```python
counts = dataERROR["status_code"].value_counts().sort_index()
bars = plt.bar(counts.index.astype(str), counts.values)

plt.title("HTTP Status Code Distribution")
plt.xlabel("Status Code")
plt.ylabel("Nber of Requests")
plt.show()
```
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/33ee3292-06e6-485f-a8a0-a57fdf14517e" />

\
\
Error requests per path \
<img width="1189" height="989" alt="image" src="https://github.com/user-attachments/assets/74f4a778-7e6f-4b90-b919-744f19fec2c8" />
