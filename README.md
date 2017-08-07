# Advanced-LUIS
This is the companion repo to the Web Hack Wednesday series 3 episode on Advanced LUIS with Gigseekr.

In the spring of 2017, we worked with [Gigseekr](http://www.gigseekr.com/) on a chat bot application that enables searching for live music events. The chat bot was written using the [Microsoft Bot Framework](https://dev.botframework.com/) and makes great use of [Language Understanding Intelligent Service (LUIS)](https://azure.microsoft.com/en-gb/services/cognitive-services/language-understanding-intelligent-service/). 

In this episode we build on the [LUIS and HowHappy.co.uk mashup](https://channel9.msdn.com/Shows/Web-Hack-Wednesday/LUIS-and-HowHappycouk-mashup) episode we did in series 2 by looking at what is new with LUIS and some of the more complex scenarios LUIS now supports - all in the context of GigSeekr.

If you want to dive deeper on the work we did with Gigseekr, you can read the full technical case study [Gigseekr builds a live music discovery bot using Bot Framework and LUIS](https://microsoft.github.io/techcasestudies/bot%20framework/cognitive%20services/2017/07/31/gigseekr.html).

## What/who is Gigseekr?
Gigseekr are a small company based in the UK who describe themselves as follows "gigseekr is a live music discovery service committed to helping you find tickets and stay up to date with tours & events across the UK".

We worked with Gigseekr on a bot for Skype, Facebook and Cortana which lets user find live music events, artists, venues and other details related to live music. You can read the full case study of the project here: [Gigseekr builds a live music discovery bot using Bot Framework and LUIS](https://microsoft.github.io/techcasestudies/bot%20framework/cognitive%20services/2017/07/31/gigseekr.html).

## LUIS Model
You can see a copy of the LUIS model we used in the show here: [GigSeekr - simple.md](GigSeekr - simple.md).

This is not the actual LUIS model used by GigSeekr, instead it is a simplified version which we use as an example for scenarios like this.

## Updated LUIS Portal and docs
In the show, we demonstrated the updated LUIS portal which you can get to at [luis.ai](https://www.luis.ai/).

We also talked about the updated and much improved documentation which you can access at [luis.ai/help](https://www.luis.ai/help). In particular, the [How to use](https://docs.microsoft.com/en-us/azure/cognitive-services/LUIS/Home) pages are great for explaining LUIS concepts.

## Entities
Gigseekr facilitate many types of search based around thw following key entities:
* Artist
* ArtistType
* EventType
* Genre
* Location
* Venue
* DateTime

## Intents
We discussed the basics of what an intent is during the [Season 2 WHW episode](https://channel9.msdn.com/Shows/Web-Hack-Wednesday/LUIS-and-HowHappycouk-mashup). In this episode we looked how Gigseekr use intents.

### Event Search
The `EventSearch` intent supports user searching for events using any combination of the entities that are supported. This intent supports utterances such as:

* `i'm looking for [ $Genre ] [ $ArtistType ] [ $EventType::Gig ] in [ $Location ] on [ $datetimeV2 ]`
* `i want to see a [ $ArtistType ] [ $EventType::Gig ] [ $Location ] on [ $datetimeV2 ]`
* `whos on at [ $Venue ]`

### Entity Search
The `EntitySearch` intent supports users searching for information on specific artists, events or venue (GigSeekr called these 'entities'). This intent supports utterances such as

* `when are [ $Artist ] next playing in [ $Location ]`
* `tell me about [ $Artist ]`
* `info on [ $Venue ]`

### Pre-built Models
We also used a pre-built domain intent around utilities which helps facilitate common utility utterances such as "Cancel", "Start again" and "Help".

Pre-built domains are a new feature in LUIS which encompass pre-built sets of intents and entities that work together for domains or common categories of apps. The pre-built domains have been pre-trained and are ready for use. The intents and entities in a pre-built domain are fully customizable once you've added them to your app - you can train them with utterances from your system so they work for your users. You can use an entire pre-built domain as a starting point for customization, or just borrow a few intents or entities from a domain for your application. 

Read more on [pre-built entities](https://docs.microsoft.com/en-us/azure/cognitive-services/LUIS/pre-builtentities) and [pre-built domains](https://docs.microsoft.com/en-us/azure/cognitive-services/LUIS/luis-how-to-use-prebuilt-domains) as well as the [Cortana pre-built app](https://docs.microsoft.com/en-us/azure/cognitive-services/LUIS/cortana-prebuilt-app).

## Features
Features are a distinguishing trait or attribute of data that your system observes. You add features to a language model, to provide hints about how to recognize input that you want to label or classify. Features help LUIS recognize both intents and entities, but features are not intents or entities themselves. Instead, features might provide examples of related terms, or a pattern to recognize in related terms. 

There are two type of feature, both of which are used in the Gigseekr model:

### Phrase List
[Phrase lists](https://github.com/Microsoft/Cognitive-Documentation/blob/master/Content/en-us/LUIS/Add-Features.md) are a list of words/phrases that belong to eth same class and should be treated similarly.

The maximum length of a phrase list is 5000 items. You may have a maximum of 10 phrase lists per LUIS app. 

Gigseekr use phrase lists to help LUIS identify Artist, ArtistType (Band, solo, rapper etc), Genre (Rocks, Blues etc), Venues and UK Locations (cities, towns, villages).

Location was implemented as a phrase list rather than the pre-built 'geography' entities because we found that the pre-built entity does not do a great job of recognising UK locations, especially smaller ones such as towns and villages. This phrase list was trained with the top 1000 uk place-names by population.

### Pattern

## Train and Test

## Summary