import discord
from discord.ext import commands
import os, random

intents = discord.Intents.default()
intents.message_content = True

tutor = ''' Tutorial Bot PlantIdea:
          1. $kemarau --> menampilkan 1 tanaman kemarau saja, ini juga akan memberi informasi selanjutnya...
         2. $hujan --> menampilkan 1 tanaman hujan saja, ini juga akan memberi informasi selanjutnya...
        3. $kemaraudanhujan --> jenis jenis tanaman hidup dimusim kemarau dan hujan
            '''

bot = commands.Bot(command_prefix='$', intents=intents)

@bot.event
async def on_ready():
    print(f'We have logged in as {bot.user}')

@bot.command()
async def hello(ctx):
    await ctx.send(f'Hi! I am a bot {bot.user}!')

@bot.command()
async def heh(ctx, count_heh = 5):
    await ctx.send("he" * count_heh)

@bot.command()
async def tutorial(ctx):
    await ctx.send(tutor)

@bot.command()
async def kemarau(ctx):
    await ctx.send(f"ini adalah jagung, tanaman kemarau, ketik $kemaraulagi untuk melihat jenis tanaman kemarau lain!")
    img_name = random.choice(os.listdir("jagung"))
    with open(f"jagung/{img_name}", "rb") as f:
        # pengenalan gambar/upload file ke discord
        picture = discord.File(f)
    # kirim file
    await ctx.send(file=picture)

@bot.command()
async def kemaraulagi(ctx):
    await ctx.send(f"ini adalah tanaman kemarau! pastikan tanaman ini tidak terlalu banyak air!")
    img_name = random.choice(os.listdir("kemarau"))
    with open(f"kemarau/{img_name}", "rb") as f:
        # pengenalan gambar/upload file ke discord
        picture = discord.File(f)
    # kirim file
    await ctx.send(file=picture)

@bot.command()
async def hujan(ctx):
    await ctx.send(f"ini adalah padi, tanaman hujan, ketik $hujanlagi untuk melihat jenis tanaman hujan lain!")
    img_name = random.choice(os.listdir("padi"))
    with open(f"padi/{img_name}", "rb") as f:
        # pengenalan gambar/upload file ke discord
        picture = discord.File(f)
    # kirim file
    await ctx.send(file=picture)

@bot.command()
async def hujanlagi(ctx):
    await ctx.send(f"ini adalah tanaman hujan! pastikan tanaman tersebut tidak terlalu kering!")
    img_name = random.choice(os.listdir("hujan"))
    with open(f"hujan/{img_name}", "rb") as f:
        # pengenalan gambar/upload file ke discord
        picture = discord.File(f)
    # kirim file
    await ctx.send(file=picture)

@bot.command()
async def kemaraudanhujan(ctx):
    await ctx.send(f"tanaman ini bisa kemarau atau hujan! pastikan kebutuhan tanaman ini harus seimbang!")
    img_name = random.choice(os.listdir("kemaraudanhujan"))
    with open(f"kemaraudanhujan/{img_name}", "rb") as f:
        # pengenalan gambar/upload file ke discord
        picture = discord.File(f)
    # kirim file
    await ctx.send(file=picture)


    





bot.run(SECRET")
