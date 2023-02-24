import requests
import discord
import json
import time 

# Twitter API endpoint for recent tweets from the Celtics account
celtics_url = "https://api.twitter.com/1.1/statuses/user_timeline.json?screen_name=@celtics&count=2"
valorleaks_url = "https://api.twitter.com/1.1/statuses/user_timeline.json?screen_name=@ValorLeaks&count=2"

# Request headers with your Twitter API credentials
headers = {
    "Authorization": "Bearer AAAAAAAAAAAAAAAAAAAAANRILgAAAAAAnNwIzUejRCOuH5E6I8xnZz4puTs%3D1Zv7ttfk8LF81IUq16cHjhLTvJu4FA33AGWWjCpTnA",
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36",
}

# Store the text of the previous tweet
previous_tweet_text = ''
previous_tweet_text1 = ''

# Function to check for new tweets and send updates to Discord
def check_celtics_tweets():
    response = requests.get(celtics_url, headers=headers)
    
    if response.status_code == 200:
        tweet = response.json()[0]
        tweet_text = tweet["text"]
        tweet_url = f"https://twitter.com/celtics/status/{tweet['id']}"
        
        global previous_tweet_text
        
        # Check if the tweet is different from the previous one
        if tweet_text != previous_tweet_text:
            
            print("New Tweet!")
            
            # Update the previous tweet text 
            previous_tweet_text = tweet_text
        
            # Discord webhook to send updates
            webhook_url = "WEBHOOK"
            
            # Discord message payload
            payload = {
                "embeds": 
                    [{
                        "title": "Celtics Tweet",
                        "description": tweet_text,
                        "color": 65280,
                        "thumbnail": {
                            "url": "https://cdn.discordapp.com/attachments/660657094130663446/1074043498497576980/celtic.png"
                        }
                        
                    }]
            }

            # Send the message to the Discord channel
            requests.post(webhook_url, json=payload)

def check_valorleaks_tweets():
    response = requests.get(valorleaks_url, headers=headers)
    
    if response.status_code == 200:
        tweet = response.json()[0]
        tweet_text = tweet["text"]
        tweet_url = f"https://twitter.com/ValorLeaks/status/{tweet['id']}"
        
        global previous_tweet_text1
        
        # Check if the tweet is different from the previous one
        if tweet_text != previous_tweet_text1:
            
            print("New Tweet!")
            
            # Update the previous tweet text 
            previous_tweet_text1 = tweet_text
        
            # Discord webhook to send updates
            webhook_url = "WEBHOOK"
            
            # Discord message payload
            payload = {
                "embeds": 
                    [{
                        "title": "Valorant Leaks",
                        "description": tweet_text,
                        "color": 0xff0000,
                        "thumbnail": {
                            "url": "https://cdn.discordapp.com/attachments/1020097717302743114/1074114440426967060/Valorant.jpg"
                        }
                        
                    }]
            }

            # Send the message to the Discord channel
            requests.post(webhook_url, json=payload)

while True:
    check_celtics_tweets()
    check_valorleaks_tweets()
    
    time.sleep(10)
    print("Searching...")
