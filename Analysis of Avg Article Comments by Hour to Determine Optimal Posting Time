#!/usr/bin/env python
# coding: utf-8

# In[3]:


from csv import reader


# In[4]:


opened_file = open('hacker_news.csv')


# In[5]:


reader_file = reader(opened_file)


# In[6]:


file_rows = list(reader_file)


# In[7]:


file = file_rows[1::]


# In[8]:


print(file_rows[0:6])


# In[9]:


header = file_rows[0:1]


# In[10]:


print(header) #this shows us what the categories are


# In[11]:


ask_posts = []
show_posts = []
other_posts = []
for row in file:
    title = row[1]
    title = title.lower()
    if title.startswith('ask hn') == True:
        ask_posts.append(row)
    elif title.startswith('show hn') == True:
        show_posts.append(row)
    else:
        other_posts.append(row)
#this code seperates the titles of articles into three categories
#of posts: ask, tell, and other


# In[12]:


#num_comments = row[4] 


# In[13]:


total_ask_comments= 0
for row in ask_posts:
    num_com = row[4]
    total_ask_comments += int(num_com)
print(total_ask_comments)
#this code shows us how many comments are present in ask posts


# In[14]:


avg_ask_com = total_ask_comments / len(ask_posts)
print(avg_ask_com) 
#this code shows how many comments an ask post receives on avg


# In[15]:


total_show_comments= 0
for row in show_posts:
    num_com = row[4]
    total_show_comments += int(num_com)
print(total_show_comments)
#this code shows us how many comments are present in show posts


# In[16]:


avg_show_com = total_show_comments / len(show_posts)
print(avg_show_com) 
#this code shows how many comments a show post receives on avg


# We can now see that on avg, ask posts receive more comments than show posts. 

# In[17]:


import datetime as dt


# In[129]:


result_list = []
for post in ask_posts:
    created_at = post[6]
    num_coms = int(post[4])
    result_list.append([created_at, num_coms])

counts_by_hour = {}
comments_by_hour = {}
for row in result_list:
    date = row[0]
    comment = row[1]
    dt_object = dt.datetime.strptime(date, "%m/%d/%Y %H:%M")
    hour = dt_object.strftime("%H")
    if hour not in counts_by_hour:
        counts_by_hour[hour] = 1
        comments_by_hour[hour] = comment
    else:
        counts_by_hour[hour] += 1
        comments_by_hour[hour] += comment 
        
        #the above code tells us the amount of ask posts and comments on ask posts per hour
print(comments_by_hour)


    
    


# In[140]:


avg_by_hour = []
for hour in comments_by_hour:
    avg_comments = comments_by_hour[hour]/counts_by_hour[hour]
    avg_by_hour.append([hour, avg_comments])


# In[208]:


print(avg_by_hour) #the above code lets us know avg comments per hour


# In[209]:


swap_avg_by_hour = []
for row in avg_by_hour:
    swap_avg_by_hour.append([row[1], row[0]])
print(swap_avg_by_hour)
#this code puts the avg num before the hour


# In[210]:


sorted_swap = sorted(swap_avg_by_hour, reverse = True)

print(sorted_swap)
#this code sorts the swap in descending order


# In[148]:


print('Top 5 hours for ask posts comments')


# In[211]:


from datetime import datetime
for time in sorted_swap:
    hour = str((time[1]))
    comms = round(time[0])
    hour_dt = str(datetime.strptime(hour,'%H'))
    hour = hour_dt[11:]
    print(hour, '-->', comms, 'average comments per post')
    #here we have a final representation of times a spost was posted and avg corresponding comments


# Final verdict: in order to have a higher chance of receiving comments on a post, one should post within the time frame of 15:00

# In[ ]:




