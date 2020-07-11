## Gatsby source plugin
This source plugin retrieves podcast data from the [Buzzprout API](https://github.com/Buzzsprout/buzzsprout-api).
The Buzzsprout api returns the list of [episodes](https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/episodes.md) for a certain podcast identified by its id.

## Usage
To use this plugin, add it to the `gatsby-config.js` file. It requires some options

```js
    {
      resolve: `gatsby-source-buzzsprout-api`
      options: {
        name: "SOMENAME",
        token: BUZZSPROUT_TOKEN,
        podcastId: "1057351",
      },
    },
```

* **name** is a string that will be used to identify the created query. It can be an empty string. This allows you to use the plugin multiple times for different podcasts
* **token** This is the [authentication token](https://github.com/Buzzsprout/buzzsprout-api#authentication) for the Buzzsprout API
* **podcastid** This is a number that identifies the podcast

After configuration is done two new queries will be available for use

* **allPodcastEpisodeSOMENAME** (where SOMENAME is the `name` option used)
* **podcastEpisodeSOMENAME**

A podcast episode data looks like this
```json
 {
    "podcastName": "SOMENAME",
    "slug":"too_small_or_too_big",
    "remoteImage": {
      ...
    },
    "id":788881,
    "title":"Too small or too big?",
    "audio_url":"https://www.buzzsprout.com/140447/788881-filename.mp3",
    "artwork_url":"https://storage.buzzsprout.com/variants/NABbMDx7JN5bSLzLPXyj67jA/8d66eb17bb7d02ca4856ab443a78f2148cafbb129f58a3c81282007c6fe24ff2",
    "description":"",
    "summary":"",
    "artist":"Muffin Man",
    "tags":"",
    "published_at":"2019-09-12T03:00:00.000-04:00",
    "duration":12362,
    "hq":true,
    "magic_mastering":true,
    "guid":"Buzzsprout788881",
    "inactive_at":null,
    "episode_number":5,
    "season_number":5,
    "explicit":false,
    "private":false,
    "total_plays":150
  },


The `remoteImage` attribute is a `remoteFileNode` created by `gatsby-source-filesystem` to optimize the `artwork_url` is meant to be used with `gatsby-plugin-sharp` and `gatsby-transformer-sharp`


## 🎓 Learning Gatsby

If you're looking for more guidance on plugins, how they work, or what their role is in the Gatsby ecosystem, check out some of these resources:

- The [Creating Plugins](https://www.gatsbyjs.org/docs/creating-plugins/) section of the docs has information on authoring and maintaining plugins yourself.
- The conceptual guide on [Plugins, Themes, and Starters](https://www.gatsbyjs.org/docs/plugins-themes-and-starters/) compares and contrasts plugins with other pieces of the Gatsby ecosystem. It can also help you [decide what to choose between a plugin, starter, or theme](https://www.gatsbyjs.org/docs/plugins-themes-and-starters/#deciding-which-to-use).
- The [Gatsby plugin library](https://www.gatsbyjs.org/plugins/) has over 1750 official as well as community developed plugins that can get you up and running faster and borrow ideas from.
