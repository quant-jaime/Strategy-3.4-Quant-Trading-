# Strategy-3.4-Quant-Trading-
#!/usr/bin/env python
# coding: utf-8

# In[30]:


import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import pandas_datareader as dr
get_ipython().run_line_magic('matplotlib', 'inline')


# In[75]:


mu = dr.data.get_data_yahoo('MU', start='2011-06-01', end = '2019-11-18')
mu.head


# In[76]:


len(mu)


# In[77]:


mu.info()


# In[78]:


mu['Close'].plot(figsize=(20,10))
plt.title('mu stock price')
plt.xlabel('date')
plt.ylabel('price')


# In[79]:


mu['Close'].plot()


# In[80]:


mu['Close'].plot(figsize=(30,15))


# In[81]:


mu['Volume'].plot()


# In[82]:


mu[['Close', "Open"]].plot()


# In[83]:


mu[['Close','Adj Close']].plot(figsize=(30,20))
plt.title('NVDA stock price for 2018')
plt.xlabel('Date')
plt.ylabel('Price')


# In[84]:


len(mu)


# In[85]:


daily_r = mu['Close']/mu['Close'].shift(1)-1
daily_r.head(50)


# In[86]:


daily_pct = mu['Close'].pct_change(1)
daily_pct.head(50)


# In[87]:


nvda_log = np.log(mu['Close']/mu['Close'].shift(1))
nvda_log.head(20)


# In[88]:


plt.plot(mu_log)


# In[89]:


mu = np.mean(nvda_log)
print(mu)


# In[90]:


sd = np.std(nvda_log)
print(sd)


# In[18]:


risk_adj = mu/sd
print(risk_adj)


# In[19]:


nvda_cum_r = (1+daily_r).cumprod()
print(nvda_cum_r)


# In[28]:


import pandas_datareader.data as web


# In[63]:


s = '2017-01-01'
e = '2019-01-01'
mu_m = dr.data.get_data_yahoo('MU', s,e, interval='m').pct_change()
m.head(50)

