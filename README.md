# Project 3 - Web APIs & NLP (Project #GetWellPlan)

### Catherine Ang, DSIF-1

### Introduction
Based on the **American Consumer Satisfaction Index (ACSI) Retail and Consumer Shipping Report 2020-2021** (released in March 2021), the retail industry (comprising supermarkets, health and personal care stores, department and discount stores, specialty retail stores, online retail and gas stations) experienced a decline in the customer satisfaction score (75.7 out of 100) in 2020 as a result of the COVID-19 pandemic – its lowest score ever since 2015.

Within the supermarkets segment, there was a 2.6% reduction in its ACSI score to 76 in 2020 (from 78 in 2019), with 17 of the 20 major brands atttaining lower customer satisfaction scores (Fig 1). **Specifically, Walmart had a 3% decline to 71 in 2020 (from 73 in 2019; scores continued to range below the average), and remained in the bottom position consecutively in 2019 and 2020**.

Source: [Russell Redman (March 2021)](https://www.supermarketnews.com/issues-trends/customer-satisfaction-fell-supermarkets-2020)


---

### Problem Statement
To **move up the ranks in ACSI 2021**, the Executive Management has requested for a thorough review of the existing customer journey at Walmart, brand image of Walmart, and aspects that need to be addressed to improve the customer experience and satisfaction level. 

As part of the Social Media Branding team at Walmart, we have been tasked to improve the company's brand image on social media sites. For a start, we will be looking into what users are saying on Walmart's Reddit page, alongside a chosen competitor – Costco – given that Costco has retained its 2nd position ranking across 2019 and 2020. 

A classification model can be developed to predict whether a Reddit post belongs to Walmart or Costco, and metrics such as accuracy, precision, recall and ROC-AUC scores can be employed to evaluate the model's performance. In addition, a sentiment analysis can be conducted to determine whether the posts have positive, neutral or negative sentiment, before arriving at the recommendations to improve the brand image online.

Essentially, this project aims to achieve the following objectives: 
- **Primary Objective**: To enhance our understanding of Walmart's brand image on Reddit, in comparison to Costco's, so as to introduce a series of strategies for improvement. 
- **Secondary Objective**: To identify positive and negative feedback from Reddit users regarding both supermarkets, where positive feedback will be reinforced and/or implemented, while negative feedback can be addressed and prevented. 

Our primary stakeholders include employees at Walmart Corporation, while our secondary stakeholders include customers of Walmart.

---

### Executive Summary


*INTRODUCTION*

With Walmart remaining in the bottom position consecutively in the supermarket segment in ACSI 2019 and 2020, this initiative aims to understand what users were saying on Walmart's social media sites in comparison to Costco, and implementing changes that can positively improve the customer experience, as well as the company's brand image online. The social media site that will be explored in this project is Reddit, which is a platform consisting of American social news, ratings for web content, and discussion forums created by users (source: [Reddit, 2021](https://www.reddit.com/)). Users are able to post contents such as images, texts, videos and links within the respective subreddits, and can express their likes/dislikes for particular posts by either voting the post up or down. 

We will be analyzing posts from the Walmart subreddit ([r/walmart](https://www.reddit.com/r/walmart/)) and Costco subreddit ([r/Costco](https://www.reddit.com/r/Costco/)). While both are well-known supermarket brands in the United States (U.S.), their different business models could have resulted in varying customer experience and brand image.



*METHODOLOGY*

A data science workflow was introduced to conduct this analysis. Firstly, the problem statement was defined — how was Walmart's brand image on Reddit like compared to Costco's, and what were the positive and negative feedback from Reddit users about both supermarkets that needed to be addressed, so as to enable Walmart to improve its brand image on social media sites and move up the ranks in ACSI 2021 with higher customer satisfaction scores. Next, the contents of the posts on Walmart and Costco subreddits were extracted via webscrapping using the Python Reddit API Wrapper (PRAW). 

Thereafter, an exploratory data analysis was conducted to identify the top one-word and two-word phrases that appeared frequently in the respective subreddit pages. New features such as the character length of the posts were engineered, and relationships between Walmart and Costco were visualized using a series of histograms, boxplots and bar charts. Concurrently, external research about the background of the commonly occurring words was carried out, to understand factors that could have affected the customer satisfaction. It was interesting to observe that Walmart's subreddit contained mainly posts from their employees, whereas those on Costco's were contributed by customers.  

A classification model was then developed, with multiple combinations of vectorizers and models being tested to predict whether a random post belonged to Walmart or Costco. Metrics such as accuracy, precision, recall and ROC-AUC scores were utilised to evaluate the models' performances. Eventually, the final combination selected was a Logistic Regression model coupled with TF-IDF (Term Frequency-Inverse Document Frequency) Vectorizer — it was capable of making predictions with an accuracy score of 78.0% *(which was 27% higher than baseline accuracy)*. A grid search was carried out to finetune the parameters used for the modelling, though it did not improve the model's accuracy further. 

Lastly, a sentiment analysis was conducted to determine whether the posts on the respective subreddit pages had positive, neutral or negative sentiment. Based on this analysis, recommendations for Walmart were compiled which included improving the employee experience first, followed by enhancing the customer journey, in order to improve the brand image online. 



*FINDINGS*

The top 10 words that identified whether a post belonged to **Walmart** were (in the order of increasing importance): 
- 'loa', 'vaccine', 'lol', 'covid', 'ppto', 'getting', 'pallet', 'store', 'associate', 'customer'.
   
On the other hand, the top 10 words that identified whether a post belonged to **Costco** were (in the order of increasing importance): 
- 'experience', 'anyone', 'online', 'good', 'delivery', 'best', 'pizza', 'food', 'membership', 'chicken'. 


The sentiment analysis revealed that Walmart's subreddit page contained 6.5% positive posts, 86.9% neutral posts and 6.6% negative posts, whereas that of Costco's contained 14.8% positive posts, 81.8% neutral posts and 3.4% negative posts. This revealed a higher proportion of Walmart's posts being identified as negative, compared to those of Costco's, and would need to be looked into to understand the source of negativity.  

---

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|author|object|walmart_posts, walmart_posts_actual|author of each post
|created_utc|float|walmart_posts, walmart_posts_actual|date and time the post is created
|id|object|walmart_posts, walmart_posts_actual|id of each post
|num_comments|integer|walmart_posts, walmart_posts_actual|number of comments each post receives
|score|integer|walmart_posts, walmart_posts_actual|number of upvotes a post has 
|selftext|object|walmart_posts, walmart_posts_actual|body text of each post
|subreddit|object|walmart_posts, walmart_posts_actual|post belongs to Walmart
|title|object|walmart_posts, walmart_posts_actual|title text of each post
|url|object|walmart_posts, walmart_posts_actual|url website for each post
|author|object|costco_posts, costco_posts_actual|author of each post
|created_utc|float|costco_posts, costco_posts_actual|date and time the post is created
|id|object|costco_posts, costco_posts_actual|id of each post
|num_comments|integer|costco_posts, costco_posts_actual|number of comments each post receives
|score|integer|costco_posts, costco_posts_actual|number of upvotes a post has 
|selftext|object|costco_posts, costco_posts_actual|body text of each post
|subreddit|object|costco_posts, costco_posts_actual|post belongs to Costco
|title|object|costco_posts, costco_posts_actual|title text of each post
|url|object|costco_posts, costco_posts_actual|url website for each post

---

### External Research

We were keen to understand why some two-word phrases appeared more commonly than others, on Walmart and Costco's subreddits.

**For Walmart:**
- **'team lead'**: A team-based operating model was introduced in Walmart in May 2019, where small teams of associates were created, cross-trained, and given more ownership of their work. (Source: [Serenah McKay (May 2019)](https://www.arkansasonline.com/news/2019/may/03/walmart-tests-new-work-hierarchy-201905/))

- **'covid vaccine'** and **'covid shot'**: Walmart, together with its membership-only retail warehouse Sam's Club, is offering customers and associates free COVID-19 vaccination administrations at their pharmacy locations nationwide, across 49 states. (Source: [Walmart Corporate (May 2021)](https://corporate.walmart.com/newsroom/2021/05/04/walmart-and-sams-club-now-administering-walk-up-covid-19-vaccines-at-5-100-pharmacies-nationwide))

- **'self checkout'**: More Walmart stores will be implementing self-checkouts in the stores, and employees who were cashiers previously would be re-assigned to other roles such as self-checkout hosts, online grocery pickups and other front ends positions, etc. (Source: [CBC News (June 2021)](https://www.cbc.ca/news/canada/british-columbia/terrace-walmart-self-checkout-1.6067061))

- **'covid leave'**: A COVID-19 emergency leave policy was introduced in March 2020, where full-time and part-time associates would receive up to two weeks of salary should they be required to stay home for COVID-19 related reasons (i.e. mandated quarantines, symptoms, illnesses, etc.). (Source: [John Furner (March 2020)](https://corporate.walmart.com/newsroom/2020/03/10/new-covid-19-policy-to-support-the-health-of-our-associates))


**For Costco:**
- **'food court'** and **'rotisserie chicken'**: Costco is known for its food court, with popular items like the quarter pound hot dog and refillable drink at USD 1.50 (price has remained the same since 1985), and rotisserie chicken at USD 4.99. (Source: [Henry Bewicke (May 2021)](https://www.talon.one/blog/what-we-can-learn-from-costcos-promotion-strategy))

- **'kirkland signature'**: Kirkland Signature is Costco's house brand, which is known for its high-quality and low-cost products, as compared to similar products from other brands. (Source: [Agela (September 2020)](https://hip2save.com/tips/brands-behind-costco-kirkland-signature/))

- **'citi card'**: The Costco Anywhere Visa® Card by Citi was introduced in May 2021, offering Costco members cashback options (ranges from 1% to 4%) across a variety of categories such as gas, restaurants and purchases from Costco. (Source: [Ryan Haar (May 2020)](https://time.com/nextadvisor/credit-cards/citi/costco-card-benefits/))

---

### Conclusion and Recommendations

We started with the **primary objective** to understand Walmart's brand image on Reddit, in comparison to Costco's, so as to introduce a series of strategies for improvement. Yet, it turns out that our associates at the stores are sharing their frustrations about the company and customers on Reddit, which will negatively affect the brand image online.
- In “The State of the American Workplace” report by Gallup, it states that employees who are engaged are more likely to improve customer relationships, with a resulting 20% increase in sales. (Source: [Shep Hyken (May 2017]( https://www.forbes.com/sites/shephyken/2017/05/27/how-happy-employees-make-happy-customers/?sh=113bc7035c35))
- Since happy employees make happy customers, it is crucial that we first look into the current employee experience and address areas that might have been overlooked.
- With happy employees, we will be able to observe positive changes to Walmart's brand image on Reddit. 
    
 
- **Our recommendations include**:
    1. Store Managers and/or Team Leads can address misconceptions that associates may have regarding COVID-19 leave, which include:
        - The 2-week COVID-19 leave is being paid for by the company; 
        - Associates who are absent because of COVID-19 related reasons will not have their attendance penalised.   
    2. Human Resource Team, Store Managers and/or Team Leads can conduct monthly or quarterly surveys for associates to provide their feedback about the working environment, working structure, salary and benefits, new team-based operating model, etc.  
    3. Human Resource Team can conduct a thorough review of the employees' compensation and benefits packages, to identify aspects that can be improved so as to provide competitive wages and benefits for associates.
    4. Human Resource Team can reinforce the fact that associates are able to [report a concern online](https://www.walmartethics.com/content/walmartethics/en_us/report-a-concern.html) without their identities being exposed, especially if they have Team Leads and/or Store Managers who are not carrying out the necessary duties.

We then looked into the **secondary objective**, which is to identify positive and negative feedback from Reddit users regarding both supermarkets, where positive feedback will be reinforced and/or implemented, while negative feedback can be addressed and prevented. 

- Since majority of the Walmart posts are shared by the employees, we will identify some of the best practices from Costco that can be potentially introduced in Walmart. 


- **Our recommendations include**: 
    1. We can engage the Product Team to look at introducing bulk items into the stores, particularly for basic necessities such as toilet paper, paper towels, water, staples like dairy and bread, proteins, disinfectant wipes, etc., and price the items at their wholesale prices. This will also allow cost savings to be passed over to customers, which is especially crucial during this pandemic. 
        - Alternatively, we can engage the Marketing Team can focus on ramping up marketing efforts for Sam's Club, which is its membership-only retail warehouse clubs that offer lower-priced warehouse products to customers. 
    2. We can also engage the Product Team to consider introducing items that provide convenience while customers are working from home, such as ready-cooked meals - the focus will be on bringing in a variety of good-quality food products to the stores, so that our customers will be spoilt for choices, and keeps them coming back for more. 
    3. Under the Walmart+ membership, apart from providing free delivery/shipping of items, selection of medical prescriptions, savings on fuel and mobile scan & go functions, we can engage the Rewards Team to look at providing discounts and rebates to members who are frequent shoppers at the stores, so as to enhance customer loyalty. (Source: [Walmart (2021)](https://www.walmart.com/plus/benefits)) 
    4. We should continue providing our curbside grocery pickup services, which provides convenience to customers who choose to pick up their items. (Source: [James Brumley (April 2021)](https://www.fool.com/investing/2021/04/11/better-buy-costco-vs-walmart/)). In addition, we should maintain our low price subscription-based grocery delivery services, as any price increase may create setbacks that prompt other grocery stores to look for alternative channels for delivery services. 
    5. In terms of building connection with customers via our brand, we can engage the Marketing Team to look at crafting marketing messages that can match the emotional tenor that our customers are experiencing during this COVID-19 pandemic. This includes messages that convey comfort, relief and hope, so as to reduce the feelings of loneliness and fear that our customers may have, and demonstrating that Walmart is here as a partner committed to helping them overcome the tough times. (Source: [Anjali Lai (March 2020)](https://go.forrester.com/blogs/consumer-energy-drops-on-all-four-dimensions-amid-covid-19/#utm_source=pr_pitch&utm_medium=pr&utm_campaign=covid19&utm_content=ConsumerEnergyIndex))
    
---

### Datasets

The sources of datasets used in this analysis: 
* [`walmart_posts_actual.csv`](./datasets/walmart_posts_actual.csv) - Walmart subreddit posts
* [`costco_posts_actual.csv`](./datasets/costco_posts_actual.csv) - Costco subreddit posts 