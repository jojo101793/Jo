## Twitter data collection and analysis

This is a project for collecting twitter data and conducting sentiment analysis on COVID-19. 

### Data collection via twitter API

Twitter API needs to be applied via [Twitter Developer](https://developer.twitter.com/en)

```markdown
# install packages
install.packages("rtweet") 
install.packages("tidytext") 
# load rtweet library
library(rtweet)
# load text mining library
library(tidytext)
```

### Collect data

```markdown
appname <- "covid"
key <- "(your api key)"
secret <- "(your api secret)"
access_token <- "(your api api token)"
access_secret <- "(your api token secret)"

# create token named "twitter_token"
twitter_token <- create_token(
  app = appname,
  consumer_key = key,
  consumer_secret = secret,
  access_token = access_token,
  access_secret = access_secret)
  
# Collect Covid-19 related tweets within Greater London 
Covid <- search_tweets("covid19 OR coronavirus* OR covid*",n =20000, geocode = "51.5,-0.08,20mi", lang = 'en')
## if you would like to collect more than 18000 tweets - use the retryonratelimit
Covid <- search_tweets("covid19 OR coronavirus* OR covid*",n =1000000, geocode = "51.5,-0.08,20mi", lang = 'en', retryonratelimit = TRUE)
## subset the dataframe - keep the information you would like to analyse
Covid <- Covid[,c('status_id','created_at','screen_name','hashtags','text','location','geo_coords')]
## drop duplicate text
Covid <- unique(Covid[ , 1:7 ] )
## save file
saveRDS(Covid,file = "Covid.rds")
```


### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

You can use the [editor on GitHub](https://github.com/jojo101793/Jo/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/jojo101793/Jo/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.
