# Assignment-5
#BanoQabil2.0
import requests
from bs4 import BeautifulSoup
import pandas as pd
url = "https://islamqa.info/en/answers/448903/repetition-of-stories-in-the-quran-with-different-wording"
page = requests.get(url)
soup = BeautifulSoup(page.content,"html.parser")
question = soup.find(class_="single_fatwa__question text-justified").text.replace("\n","").replace("Question","")
answer = soup.find(class_="content").text.replace("\n","")
data = [[url,question,answer]]
df = pd.DataFrame(data,columns=['url','question','answer'])
df.to_csv("Assignment#5.csv")
