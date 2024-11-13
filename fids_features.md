# fid_features

Aggregates data about every user for the last 30 days. Unless otherwise specified, all column descriptions are based on the last 30 days.

[Dune link](https://dune.com/queries/4232751)

*Updated every 24 hours*

|Column|Type|Description|
|---|---|---|
|fid|INTEGER|User id|
|user_registered_at|TIMESTAMP|Timestamp of account registration|
|user_address|STRING|User's associated Ethereum address|
|user_name|STRING|Username|
|user_pfp|STRING|User's profile picture URL|
|---|---|---|
|follower_num|INTEGER|Number of followers|
|following_num|INTEGER|Number of following|
|---|---|---|
|is_active|BOOLEAN|Any activity in the last 30 days|
|---|---|---|
|casts_all_first|TIMESTAMP|Timestamp of first recorded cast ever|
|casts_all_last|TIMESTAMP|Timestamp of last recorded cast ever|
|casts_all_num|INTEGER|Number of casts (ever)|
|casts_all_del|INTEGER|Number of casts deleted (ever)|
|---|---|---|
|casts30d_active_days|INTEGER|Number of days with some activity|
|casts30d_num|INTEGER|Number of casts|
|casts30d_num_in_channels|INTEGER|Number of casts in channels|
|casts30d_replies|INTEGER|Number of replies|
|casts30d_del|INTEGER|Number of casts deleted|
|casts30d_del_ratio|INTEGER|Ratio of deletions to casts|
|---|---|---|
|channels|STRING|List of channels the user has casted in|
|---|---|---|
|react_out_num|INTEGER|Number of reactions sent|
|react_out_del|INTEGER|Number of reactions deleted|
|react_out_likes|INTEGER|Number of likes sent|
|react_out_recasts|INTEGER|Number of recasts sent|
|react_out_ufids|INTEGER|Number of unique users whom the user has sent reactions to|
|react_out_del_ratio|REAL|Reaction delete ratio|
|---|---|---|
|react_in_num|INTEGER|Number of reactions received|
|react_in_del|INTEGER|Number of reactions received then deleted|
|react_in_likes|INTEGER|Number of likes received|
|react_in_recasts|INTEGER|Number of recasts received|
|react_in_ufids|INTEGER|Number of unique users who reacted to the user|
|---|---|---|
|replies_num|INTEGER|Number of replies received|
|replies_del|INTEGER|Number of replies received then deleted|
|replies_ufids|INTEGER|Number of unique users who replied to the user|
|---|---|---|
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
|---|---|---|
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
|---|---|---|
|lang_1|STRING|Primary language|
|lang_2|STRING|Second language|
|---|---|---|
|keywords|STRING|Top 50 words and frequencies in the user activity, including casts, recasts, likes and replies, weighted the same way as preferences|
|---|---|---|
|time_reply|REAL|Average time to reply in hours|
|time_react|REAL|Average time to react in hours|
|spam_time|REAL|Average time to reply or react in hours|
|spam_daily_casts|REAL|Average number of casts per day|
|spam_delete_ratio|REAL|Ratio of deletes to actions across casts, replies and reactions|
|spam_time_flag|BOOLEAN|Flags accounts where the time between messages is below the 5th percentile|
|spam_daily_casts_flag|BOOLEAN|Flags accounts where messages per day is above the 95th percentile|
|spam_delete_ratio_flag|BOOLEAN|Flags accounts where deletes per day is above the 95th percentile|
|spam_any_flags|INTEGER|Flags accounts where any of the above 3 flags are true|
