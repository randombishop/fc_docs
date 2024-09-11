# Big Query Dataset

So far, the following tables are available:
* cast_features
* fid_features
* followers
* reactions
* fid_username
* username_fid

This dataset can be queried directly from the [web app](https://app.datascience.art/#/bot) or by tagging @dsart on Farcaster.


## cast_features

### Description
Contains cast data since June, 1st 2024, enriched with categories, topics, embeddings, and ML features.

### Primary Key
hash

### Paritioning
By *day*

### Clustering
By *fid*

### Columns

|Column|Type|Description|
|---|---|---|
|day|DATE|YYYY-MM-DD|
|timestamp|TIMESTAMP|Cast timestamp as recorded by the Farcaster hub.|
|hash|STRING|Cast hash.|
|fid|INTEGER|Author fid.|
|user_name|STRING|Author username at time of cast.|
|num_follower|INTEGER|Author's number of followers at time of cast.|
|num_follower_bin|num_follower bin from 0 to 9, based on the same hour distribution.|
|num_following|INTEGER|Author's number of followed accounts at time of cast.|
|num_following_bin|num_following bin from 0 to 9, based on the same hour distribution.|
|num_casts_same_hour|INTEGER|Number of times the user casted in the same hour.|
|text|STRING|Cast text.|
|text_len|INTEGER|Cast text length.|
|text_len_bin|INTEGER|text_len bin from 0 to 9, based on the same hour distribution.
|embeds|JSON|Array of embeddings as recorded by the Farcaster hub.
|mentions|JSON|Array of mentions. As recorded by the Farcaster hub.
|mentions_pos|JSON|Array of mentions positions. As recorded by the Farcaster hub.
|embeds_num|INTEGER|Number of embeddings.
|mentions_num|INTEGER|Number of mentions.
|parent_fid|INTEGER|Parent cast fid when it's a reply.
|parent_hash|STRING|Parent cast hash when it's a reply.
|parent_url|STRING|Parent url when it's casted in a channel.
|category|INTEGER|Category classification into one of 11 categories.
|category_label|STRING|Category label, one of c_arts, c_business, c_crypto, c_culture, c_misc, c_money, c_nature, c_politics, c_sports, c_tech_science.
|topic|INTEGER|Topic classification into one of 60 topics.
|topic_label|STRING|Topic label.
|q_clear|INTEGER|Is it clear? (from 0 to 100)
|q_audience|INTEGER|Does it have a clear target audience? (from 0 to 100)
|q_info|INTEGER|Is it informative? (from 0 to 100)
|q_easy|INTEGER|Is it easy to understand for the general layman public? (from 0 to 100)
|q_verifiable|INTEGER|Is it verifiable online? (from 0 to 100)
|q_personal|INTEGER|Is it personal? (from 0 to 100)
|q_funny|INTEGER|Is it funny? (from 0 to 100)
|q_meme_ref|INTEGER|Is it a reference to a well known meme? (from 0 to 100)
|q_emo_res|INTEGER|Does it elicit an emotional response? (from 0 to 100)
|q_happiness|INTEGER|Does it convey happiness? (from 0 to 100)
|q_curiosity|INTEGER|Does it trigger curiosity? (from 0 to 100)
|q_aggressivity|INTEGER|Is it aggressive? (from 0 to 100)
|q_surprise|INTEGER|Does it have an element of surprise? (from 0 to 100)
|q_interesting_ask|INTEGER|Does it ask an interesting question? (from 0 to 100)
|q_call_action|INTEGER|Does it come with an explicit call to action? (from 0 to 100)
|c_xxx|INTEGER|c_columns indicate how likely the cast is to be in that category. (from 0 to 100)
|t_xxx|INTEGER|t_columns indicate how likely the cast is to be in that topic. (from 0 to 100)
|dim_1 to dim_32|FLOAT|Reduced embedding dimensions. These were calculated such that, when combined with the q_, c_ and t_ features, will conserve as much information from the 512 embedding as possible.
|h01_deleted|TIMESTAMP|Deletion timestamp if the cast was deleted within 1 hour?
|h01_likes|INTEGER|Number of likes within 1 hour.
|h01_recasts|INTEGER|Number of recasts within 1 hour.
|h01_replies|INTEGER|Number of replies within 1 hour.
|h12_deleted|TIMESTAMP|Deletion timestamp if the cast was deleted within 12 hours?
|h12_likes|INTEGER|Number of likes within 12 hours.
|h12_recasts|INTEGER|Number of recasts within 12 hours.
|h12_likes|INTEGER|Number of likes within 12 hours.
|h12_replies|INTEGER|Number of replies within 12 hours.
|h36_deleted|TIMESTAMP|Deletion timestamp if the cast was deleted within 36 hours?
|h36_likes|INTEGER|Number of likes within 36 hours.
|h36_recasts|INTEGER|Number of recasts within 36 hours.
|h36_replies|INTEGER|Number of replies within 36 hours.
|predict_like|INTEGER|Output of the Likemeter model (0 to 100).


## fid_features

### Description
Aggregates data about every user for the last 30 days. Unless otherwise specified, all column descriptions are based on the last 30 days.

### Primary Key
*fid*

### Clustering
By *fid*

### Columns

|Column|Type|Description|
|---|---|---|
|day|DATE|Time of generation, should be yesterday|
|fid|INTEGER|User id|
|first_cast|TIMESTAMP|Timestamp of first recorded cast (not 30-day bound)|
|last_cast|TIMESTAMP|Timestamp of last recorded cast (not 30-day bound)|
|num_casts|INTEGER|Number of casts in total (not 30-day bound)|
|user_name|STRING|Username|
|msg_num_days|INTEGER|Number of days with some activity|
|msg_messages|INTEGER|Number of messages submitted, includes casts, recasts, likes, replies, follows, and deletes|
|msg_messages_per_day|FLOAT|Average number of messages per day, when active.|
|msg_casts|INTEGER|Number of casts|
|msg_replies|INTEGER|Number of replies|
|msg_casts_in_channels|INTEGER|Number of casts in channels|
|msg_delete_casts|INTEGER|Number of deleted casts|
|msg_likes|INTEGER|Number of likes sent|
|msg_recasts|INTEGER|Number of recasts sent|
|msg_delete_reactions|INTEGER|Number of deleted reactions|
|msg_follows|INTEGER|Number of follow actions|
|msg_delete_follows|INTEGER|Number of deleted follows|
|msg_avg_time_any|FLOAT|Average time between any like, recast or reply and its target cast|
|msg_avg_time_react|FLOAT|Average time to like or recast a cast|
|msg_avg_time_reply|FLOAT|Average time to reply to a cast|
|msg_total_deletes|INTEGER|Total number of deletes|
|msg_ratio_deletes|FLOAT|Ratio of deleted messages to total messages|
|msg_active|INTEGER|Same as (number of messages > 0)|
|spam_messages_per_day|INTEGER|Flags accounts where messages per day is above the 95th percentile|
|spam_deletes|INTEGER|Flags accounts where deletes per day is above the 95th percentile|
|spam_speed|INTEGER|Flags accounts where the time between messages is below the 5th percentile|
|spam_any|INTEGER|Flags accounts where any of the above conditions are true|
|followers_num|INTEGER|Number of followers|
|following_num|INTEGER|Number of following|
|eng_num_days|INTEGER|Number of days where the user received some engagement|
|eng_likes|INTEGER|Number of likes received|
|eng_recasts|INTEGER|Number of recasts received|
|eng_replies|INTEGER|Number of replies received|
|eng_ufids_likes_ratio|FLOAT|Ratio of unique users who liked to total likes|
|eng_ufids_recasts_ratio|FLOAT|Ratio of unique users who recasted to total recasts|
|eng_ufids_replies_ratio|FLOAT|Ratio of unique users who replied to total replies|
|prefs_num_days|INTEGER|Number of days where we recorded user preferences|
|prefs_q_clear|FLOAT|Scores user preference for clear content|
|prefs_q_audience|FLOAT|Scores user preference for clear audience|
|prefs_q_info|FLOAT|Scores user preference for informative casts|
|prefs_q_easy|FLOAT|Scores user preference for easy to understand content|
|prefs_q_verifiable|FLOAT|Scores user preference for verifiable content|
|prefs_q_personal|FLOAT|Scores user preference for personal content|
|prefs_q_funny|FLOAT|Scores user preference for funny content|
|prefs_q_meme_ref|FLOAT|Scores user preference for meme references|
|prefs_q_emo_res|FLOAT|Scores user preference for emotional content|
|prefs_q_happiness|FLOAT|Scores user preference for happy sentiment content|
|prefs_q_curiosity|FLOAT|Scores user preference for content that triggers curiosity|
|prefs_q_aggressivity|FLOAT|Scores user preference for aggressive content|
|prefs_q_surprise|FLOAT|Scores user preference for content with an element of surprise|
|prefs_q_interesting_ask|FLOAT|Scores user preference for content that asks an interesting question|
|prefs_q_call_action|FLOAT|Scores user preference for content that calls to action|
|prefs_c_arts|FLOAT|User preference for category: arts|
|prefs_c_business|FLOAT|User preference for category: business|
|prefs_c_crypto|FLOAT|User preference for category: crypto|
|prefs_c_culture|FLOAT|User preference for category: culture|
|prefs_c_misc|FLOAT|User preference for category: misc|
|prefs_c_money|FLOAT|User preference for category: money|
|prefs_c_na|FLOAT|User preference for category: na|
|prefs_c_nature|FLOAT|User preference for category: nature|
|prefs_c_politics|FLOAT|User preference for category: politics|
|prefs_c_sports|FLOAT|User preference for category: sports|
|prefs_c_tech_science|FLOAT|User preference for category: tech_science|
|prefs_total_weight|INTEGER|Total weight used to calculate preferences, casts are worth 4, recasts: 3, likes: 2, replies: 1|
|prefs_category|STRING|Top category in preferences|
|lang_1|STRING|Primary language|
|lang_2|STRING|Second language|
|words_dict|STRING|Top 50 words and frequencies in the user activity, including casts, recasts, likes and replies, weighted the same way as preferences|


## followers

### Description
Aggregated representation of the social graph.
Contains one row per follower/followed pair with the last timestamps of addition and removal.

### Paritioning
None

### Clustering
fid_followed/fid_follower

### Columns

|Column|Type|Description|
|---|---|---|
|fid_follower|INTEGER|Follower User ID|
|fid_followed|INTEGER|Followed User ID|
|added_at|TIMESTAMP|Followed at latest timestamp|
|removed_at|TIMESTAMP|Unfollowed at latest timestamp|



## reactions

### Description
Another interesting representation of the social graph.
Contains one row per source/target user pair with the total number of replies, likes, and recasts.

### Paritioning
None

### Clustering
fid/target_fid

### Columns

|Column|Type|Description|
|---|---|---|
|fid|INTEGER|Source User ID|
|target_fid|INTEGER|Target User ID|
|num_replies|INTEGER|Number of replies|
|num_likes|INTEGER|Number of likes|
|num_recasts|INTEGER|Number of recasts|



## fid_username

### Description
Maps fids to usernames, and adds a couple of stats about the user: first/last cast timestamp and number of casts.

### Paritioning
None

### Clustering
fid

### Columns

|Column|Type|Description|
|---|---|---|
|fid|INTEGER|User ID|
|first_cast|TIMESTAMP|First cast timestamp|
|last_cast|TIMESTAMP|Last cast timestamp|
|num_casts|INTEGER|Number of casts|
|user_name|STRING|Username|


## username_fid

### Description
Since Big Query does not support multipe index per table, this is just another table to map from username to fid without the need to do a full scan of fid_username table.

### Paritioning
None

### Clustering
user_name

### Columns

|Column|Type|Description|
|---|---|---|
|user_name|STRING|Username|
|fid|INTEGER|User ID|
