# Youtube-Scrapping
#Scrapping youtube videos details using python

import json
import os
import requests
from pytube import YouTube

url = "https://www.youtube.com/watch?v=h8tYHN1j0lQ&feature=emb_logo&ab_channel=DoordarshanSahyadri"
Vid={}
Link = url
source= requests.get(url).text
soup=BeautifulSoup(source,'html.parser')
div_s = soup.findAll('div')
Title = div_s[1].find('span',id="info-contents",attrs={'class':"style-scope ytd-watch-flexy"} )
Vid['Title']=Title
Vid['Link']=Link

Channel_name = div_s[1].find('span',class_="yt-simple-endpoint style-scope yt-formatted-string")
Channel_link = (url)
Subscribers = div_s[1].find('a',class_="style-scope ytd-video-owner-renderer")

Vid['Channel']=Channel_name
Vid['Channel_link']=Channel_link
Vid['Channel_subscribers']=Subscribers

View_count = div_s[1].find(class_= 'view-count style-scope yt-view-count-renderer')
Vid['Views']=View_count

Likes = div_s[1].find('button',class_="yt-simple-endpoint style-scope ytd-toggle-button-renderer" )
Vid['Likes']=Likes
Dislikes = div_s[1].find('button',class_="yt-simple-endpoint style-scope ytd-toggle-button-renderer" )
Vid['Dislikes']=Dislikes

print('Title of the video url:', Title)
print('Channel :', Channel_name)
print('Link:', Channel_link)
print('Number of Subscibers:', Subscribers)
print('View count for video:', View_count)
print('Likes:',Likes,'  ','Dislikes:',Dislikes)
