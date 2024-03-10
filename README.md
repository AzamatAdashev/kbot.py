import discord
from discord.ext import commands
import os
import random
intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix='!', intents=intents)
@bot.command()
async def mem(ctx):
    images_lst = os.dirlist('images')
    with open(f'images/{random.choice(images_lst)}', 'rb') as f:
        # В переменную кладем файл, который преобразуется в файл библиотеки Discord!
        picture = discord.File(f)
   # Можем передавать файл как параметр!
    await ctx.send(file=picture)
bot.run()
