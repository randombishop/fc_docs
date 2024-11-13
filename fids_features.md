# fid_features

Aggregates data about every user for the last 30 days. Unless otherwise specified, all column descriptions are based on the last 30 days.

[Dune link](https://dune.com/queries/4232751)

*Updated every 24 hours*

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

