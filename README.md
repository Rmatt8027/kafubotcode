import discord
from discord.ext import commands
#pip install requests
import discord_buttons_plugin
import requests

bot = commands.Bot(command_prefix="!", intents=discord.Intents.all())


#起動したときに起こるイベント
@bot.event
async def on_ready():
    print("準備完了")
    await bot.tree.sync()


#!bw
@bot.command()
async def bw(ctx):
    await ctx.send("@here みんなーBEDWARSの募集がかけられてるよーー　みんなVCに集まれーー")


#!bedwars
@bot.command()
async def bedwars(ctx):
    await ctx.send("@here みんなーBEDWARSの募集がかけられてるよーー　みんなVCに集まれーー")


#!mineman
@bot.command()
async def mineman(ctx):
    await ctx.send("@here みんなーMINEMANの募集がかけられてるよーー　みんなVCに集まれーー")


#!rearth
@bot.command()
async def rearth(ctx):
    await ctx.send("@here みんなーラース鯖の募集がかけられてるよーー　みんなVCに集まれーー")

@bot.command()
async def update(ctx):
    view = discord.ui.View()
    view.add_item(discord.ui.Button(label="ver 1.2", style=discord.ButtonStyle.green, custom_id="ver1_2"))
    view.add_item(discord.ui.Button(label="ver 1.1", style=discord.ButtonStyle.green, custom_id="ver1_1"))
    view.add_item(discord.ui.Button(label="ver 1.0", style=discord.ButtonStyle.blue, custom_id="ver1_0"))
    await ctx.send(view=view)

@bot.event
async def on_interaction(interaction: discord.Interaction):
    try:
        if interaction.data["component_type"] == 2:
            if interaction.data["custom_od"] == "ver1_2":
                await interaction.response.send.message("Ver.1.2 Changelog: Changelogの追加", ephemeral=Ture)
            if interaction.data["custom_od"] == "ver1_1":
                await interaction.response.send.message("Ver.1.1 Changelog: !bedwars, !rearth, !minemanコマンドの追加(バグ修正)", ephemeral=Ture)
            if interaction.data["custom_id"] == "ver1_0":
                await interaction.response.send.message("Ver.1.0 Changelog: !bwコマンドの追加(バグ多数)", ephemeral=Ture)
    except KeyError:
        pass


bot.run("MY TOKEN")
