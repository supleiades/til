# discord.ext.tasks

指定した間隔でバックグラウンドでループを実行させる

# コグ

https://discordpy.readthedocs.io/ja/latest/ext/commands/cogs.html?highlight=cog

# 目的別

## メッセージを送信

```
message.channel.send()
```

## テキストに指定文字列が含まれている場合に実行するif文

```
async def on_message(message):
    if message.content == '{指定文字列}';
```

## ボットのコマンド
```
# プレフィックスは/
# コマンドはneko
bot = commands.Bot("/")
@bot.command()
async def neko(ctx):
    await ctx.send(f'{ctx.author.mention} にゃーん')
```
