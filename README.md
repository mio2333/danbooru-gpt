# danbooru-gpt
GPT2 Model Trained On Millions Tags Of Danbooru Datasets.

It can used for tags sampling for test.

## Datasets Preparation

Danbooru Datasets can be downaloaded through https://gwern.net/danbooru2021

For this project,only metadata is needed for download.

metadata contains 2017-2021 years tags data,and every file type is jsonl 

each data is like:
```json
{"id":"263162","created_at":"2008-06-10 03:08:07.34205 UTC","uploader_id":"65792","score":"1","source":"","md5":"9a0f9e0f08907d12b7d08e46047ae4d8","last_commented_at":"1970-01-01 00:00:00 UTC","rating":"s","image_width":"797","image_height":"794","is_note_locked":false,"file_ext":"jpg","last_noted_at":"1970-01-01 00:00:00 UTC","is_rating_locked":false,"parent_id":"0","has_children":false,"approver_id":"1309","file_size":"110256","is_status_locked":false,"up_score":"1","down_score":"0","is_pending":false,"is_flagged":false,"is_deleted":false,"updated_at":"2016-04-23 14:32:09.52181 UTC","is_banned":false,"pixiv_id":"0","tags":[{"id":"540830","name":"1boy","category":"0"},{"id":"470575","name":"1girl","category":"0"},{"id":"16751","name":"bangs","category":"0"},{"id":"537684","name":"blunt_bangs","category":"0"},{"id":"16867","name":"brown_hair","category":"0"},{"id":"488","name":"flute","category":"0"},{"id":"454933","name":"hair_bun","category":"0"},{"id":"446622","name":"hime_cut","category":"0"},{"id":"464564","name":"instrument","category":"0"},{"id":"1707","name":"japanese_clothes","category":"0"},{"id":"395796","name":"kakinouchi_narumi","category":"1"},{"id":"576631","name":"larva_(vampire_princess_miyu)","category":"4"},{"id":"13197","name":"long_hair","category":"0"},{"id":"1797","name":"mask","category":"0"},{"id":"1287928","name":"miyu_(vampire_princess_miyu)","category":"4"},{"id":"464575","name":"ribbon","category":"0"},{"id":"15189","name":"vampire_princess_miyu","category":"3"},{"id":"89189","name":"yellow_eyes","category":"0"}],"pools":[],"favs":["15115","159766","23892"]}
```
For our purpose, only tags key and it's value is useful.

According to [danbooru wiki](https://danbooru.donmai.us/wiki_pages/help:tags)'s help, we can know there are five category for tags: `Artist`,`Character`,`Copyright`,`Meta`,`General`.

For our purpose,only General tags are useful because we want to build a general language model for Danbooru tags,not specific for any character or other things.

So every tags is like:
```txt
1girl,brown_eyes,brown_hair,copyright_name,dress,fighting_stance,full_body,green_eyes,looking_at_viewer,red_dress,short_hair,solo,text_focus
```

So I extract these tags to a raw datasets using huggingface **datasets** and get **4,790,560** tags, then push it to huggingface. The link is https://huggingface.co/datasets/mio/danbooru2021-tags.


`
