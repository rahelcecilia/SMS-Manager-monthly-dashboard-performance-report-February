# SMS Manager Monthly Dashboard Performance Report (February)

Processing raw monthly datasets on broadcast message delivery to identify insights and analyze the company's growth trends. <br>

### Technologies Used:
<li>Python (Pandas) – Data Cleaning, Handling Missing & Duplicate Values</li> <br>

<pre>import pandas as pd 
df = pd.read_csv('vgsales.csv') <br>
<strong> # Missing Values</strong>
df.isna().sum() <br>
<strong> # Duplicate Values</strong>
duplicate_rows = df[df.duplicated()]<br>
<strong> #Export</strong>
df.to_excel("february.xlsx") </pre>

<li>Power BI – DAX, Filter, Chart (Bar, Pie, Line)</li>
<br>
<pre><strong> Data Analysis Expressions (DAX) </strong> 
<strong>#Create a new column that contains the time difference of message delivery.</strong>
    SelisihDetik = DATEDIFF('Sheet1'[TrxDateTime], 'Sheet1'[SentDateTime], SECOND) <br>
<strong>#Create a new column that categorizes the time difference.</strong>
  KategoriSelisih = 
    SWITCH(
        TRUE(),
        'Sheet1'[SelisihDetik] <= -1, 0,
        'Sheet1'[SelisihDetik] = 0, 0,
        'Sheet1'[SelisihDetik] = 1, 1,
        'Sheet1'[SelisihDetik] = 2, 2,
        'Sheet1'[SelisihDetik] = 3, 3,
        'Sheet1'[SelisihDetik] = 4, 4,
        'Sheet1'[SelisihDetik] = 5, 5
          ) <br>
<strong>#Split the timestamp column into hour, second, and minute.</strong>
          Jam = HOUR('Sheet1'[SentDateTime])
          Jam = MINUTE('Sheet1'[SentDateTime])
          Jam = SECOND('Sheet1'[SentDateTime]) <br> </pre>

### Key Features : <br>
<li><strong>Date Filter</strong> – Allows users to select specific dates for analysis.</li>
<li><strong>Total Messages Sent</strong> – Summarizes the total number of messages sent during the period.</li>
<li><strong>Total Delivered Messages</strong> – Displays the total number of successfully delivered messages.</li>
<li><strong>Total Undelivered Messages</strong> – Shows the number of messages that failed to be delivered.</li>
<li><strong>Delivery Success Rate Breakdown</strong> – A pie chart illustrating the proportion of delivered and undelivered messages.</li>
<li><strong>Total Messages per Hour</strong> – Shows the number of delivered and undelivered messages by hour, helping identify peak messaging times.</li>
<li><strong>Delivery Time Difference (in Seconds)</strong> – Displays the distribution of delivery times, showing how long messages take to be delivered.</li>


<br> 

![image](https://github.com/user-attachments/assets/ad38e4b3-8024-478a-adda-db576afed56a)



