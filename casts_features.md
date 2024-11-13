# Casts Features

Contains cast data since November, 1st 2024, enriched with categories, topics, embeddings, and ML features.

[Dune link](https://dune.com/queries/4280808)

*Updated every 2 hours, lagging 2 to 3 hours behind real time data.*

|Column|Type|Description|
|---|---|---|
|day|DATE|YYYY-MM-DD|
|timestamp|TIMESTAMP|Cast timestamp as recorded by the Farcaster hub.|
|hash|STRING|Cast hash.|
|fid|INTEGER|Author fid.|
|user_name|STRING|Author username at time of cast.|
|user_pfp|STRING|Profile picture URL.|
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
|predict_like|INTEGER|Output of the Likemeter model (0 to 100).

